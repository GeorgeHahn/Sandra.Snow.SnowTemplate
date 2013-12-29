---
layout: post
title: Ugly Duck Model Binding in Nancy 
---
It's been a while since I last wrote about my pet web development project. I have made a couple large changes - most importantly, I am now using RavenDB. The second big change is that I have begun dual booting Windows 8 as my development system. While running Windows in a VM is enough to get into Visual Studio, the little pauses began to drive me crazy. I went out and bought a 240 GB Corsair Force GT and couldn't be happier.

Onto my main reason for writing this post - data binding!

I ran into an issue when attempting to bind a HTTP POST to a complex type. The type I was attempting to bind to was *QuestionModel*, as defined below.
	
	public class QuestionModel
	{
	 public string Question;
	 public List<AnswerModel> Answers;
	 public int CorrectAnswer;
	 public string Section;
	}
	 
	public class AnswerModel
	{
	 public int Id;
	 public ChemicalModel ChemicalModel;
	}
	 
	public class ChemicalModel
	{
	 public string SMILESString;
	}

Binding to the base *QuestionModel* variables was no problem, *this.Bind<QuestionModel>()* worked great. The problem came about in binding to the *List of AnswerModels* - namely, in that binding simply didn't happen. After a lot of searching, I came across a [StackOverflow post](http://stackoverflow.com/questions/11649385/nancy-model-binding-to-child-class) regarding binding to types with complex children. It looks like the proper way to handle this situation is to write a custom model binder. One alternative I did not investigate was POSTing a JSON object.

Rather than do things the right way, I chose to apply some ugly duck tape.
	
	Post["/add"] = o =>
	 {
	  // Doesn't bind much
	  var question = this.Bind<QuestionModel>();
	 
	  // Bind the rest
	  for (int i = 0; i < 20; i++) // Bind a max of 20 children
	  {
	   bool hitSomething = false;
	   if (Request.Form["Answers[" + i + "].AnswerString"] != null) // Bind the AnswerString property
	   {
	    while (question.Answers.Count <= i) // If the index doesn't exist yet, create it and every index before
	     question.Answers.Add(new AnswerModel());
	    question.Answers[i].AnswerString = Request.Form["Answers[" + i + "].AnswerString"];
	    hitSomething = true;
	   }
	 
	   if (Request.Form["Answers[" + i + "].SMILESString"] != null) // Bind the SMILESString property
	   {
	    while (question.Answers.Count < i - 1)
	     question.Answers.Add(new AnswerModel());
	    question.Answers[i].ChemicalModel =
	     new ChemicalModel(Request.Form["Answers[" + i + "].SMILESString"]);
	    hitSomething = true;
	   }
	   if (!hitSomething)
	    break;
	  }
	 
	  DocumentSession.Store(question);
	  DocumentSession.SaveChanges();
	 
	  Model.question = question;
	  return View["ShowQuestion", Model];
	 };

This is going to come back to bite me shortly, but it is adequate for the time being. I suppose the moral of the story today is that if you find yourself needing a model binder that is capable of binding to array-indexed names, bother me - hopefully I'll have written it by the time you read this. 