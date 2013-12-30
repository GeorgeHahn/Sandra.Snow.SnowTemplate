---
layout: post
title: Journal: Database is Finally Working and Enabling Sessions.       
category: words
---
**Finally**, I can write some code. First things first, though, here's what I had to do to get to this point.

I am running on a fairly fresh Windows 8 virtual machine with VS2012.

Installed EF5, Nancy, and Nancy.Hosting.Aspnet from NuGet.

Added this to web.config

	<connectionStrings>
	  <add name="QAContext" 
	    providerName="System.Data.SqlClient"
	    connectionString="Server=(LocalDB)\v11.0; Integrated Security=True; MultipleActiveResultSets=True"/>
	</connectionStrings> 


If memory serves, that's all it took. My sample code looks something like this

	using (var db = new QAContext())
	{
	    var user = new User();
	    user.Name = userName;
	    db.Users.Add(user);
	    db.SaveChanges();
	}


And it runs! I can query db with LINQ (though I am not very skilled with LINQ), and view the database in the Server Explorer window.

Now, I'm going to enable cookie based sessions. To do this, I'll subclass DefaultNancyBootstrapper and override the ApplicationStartup method.

	public class Bootstrapper: DefaultNancyBootstrapper
	{
	    protected override void ApplicationStartup(TinyIoCContainer container,
	                                               IPipelines pipelines)
	    {
	        CookieBasedSessions.Enable(pipelines);
	    }
	}

 

With sessions enabled, we can now put something like this in the constructor of a class that derives from NancyModule to test sessions.

	Get["/sessiontest/{val}"] = parameters => { 
	    Session["test"] = parameters.val.ToString();
	    return Session["test"].ToString();
	};
	 
	Get["/sessiontest"] = parameters => Session["test"].ToString();

 

Now localhost/sessiontest/testtesttest will show "testtesttest" and http://localhost:15818/sessiontest will show the same. 