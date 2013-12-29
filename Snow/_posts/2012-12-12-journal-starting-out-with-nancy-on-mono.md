---
layout: post
title:  Journal: Starting out with Nancy on Mono Pt.1 
---
Before starting out, I installed NuGet, per these combined instructions:

[http://monomvc.wordpress.com/2012/03/06/nuget-on-mono/](http://monomvc.wordpress.com/2012/03/06/nuget-on-mono/) <br/>
[http://grhughes.com/32/using-nuget-in-mono](http://grhughes.com/32/using-nuget-in-mono) <br/>
[http://nuget.codeplex.com/workitem/1271](http://nuget.codeplex.com/workitem/1271)

Special note on the last item there. I had to put Microsoft.Build.dll into the same directory as NuGet.exe before it would run. (Was failing for 'Could not load type 'NuGet.Commands.ProjectFactory')


Now that I was ready to move on to some code, I created a new C# ASP.NET project in MonoDevelop. I'm using MonoDevelop 3.0.5 that I built from source, but all other versions should have this option.

I downloaded the latest Nancy build from their CI server here:
[http://teamcity.codebetter.com/project.html?projectId=project112&tab=projectOverview&guest=true](http://teamcity.codebetter.com/project.html?projectId=project112&tab=projectOverview&guest=true)

Added references to Nancy.dll and Nancy.Hosting.Aspnet.dll in MonoDevelop.


On the Nancy wiki's into page, there is a Hello World snippet. Before running it, a web.config file must be created.

I found the default configuration here: https://github.com/NancyFx/Nancy/wiki/Hosting-nancy-with-asp.net

	<configuration>
	  <system.web>
	    <compilation debug="true" targetFramework="4.0" />
	    <httpHandlers>
	      <add verb="*" type="Nancy.Hosting.Aspnet.NancyHttpRequestHandler" path="*"/>
	    </httpHandlers>
	  </system.web>
	
	  <system.webServer>
	    <modules runAllManagedModulesForAllRequests="true"/>
	    <validation validateIntegratedModeConfiguration="false"/>
	    <handlers>
	      <add name="Nancy" verb="*" type="Nancy.Hosting.Aspnet.NancyHttpRequestHandler" path="*"/>
	    </handlers>
	  </system.webServer>
	</configuration>


Pressed *Start program without debugging* and watched magic happen! 