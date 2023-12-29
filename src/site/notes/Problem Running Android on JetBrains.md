---
{"dg-publish":true,"permalink":"/problem-running-android-on-jet-brains/"}
---


	Error running 'Project.Mobile.App.Android'
	Failed to deploy: there is no package com.company.project.section.app in the list of installed packages

## Solution
- Change package on AndroidManifest.xml and limit the terms to 4 strings
	- eg. com.company.project.app
	- Donot: com.company.project.section.app
