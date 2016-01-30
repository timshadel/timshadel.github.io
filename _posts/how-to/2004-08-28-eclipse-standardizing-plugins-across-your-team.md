---
title: '[Eclipse] Standardizing plugins across your team'
author: Tim
layout: post
redirect_from:
  - /2004/08/28/eclipse-standardizing-plugins-across-your-team/
  - /blog/2004/08/28/1093715447000.html
category:  How-To
tags:
  - eclipse
---
We&#8217;ve got several developers (more than 5) at work using [Eclipse][1], and some are pretty new at it. We gave each a list of the plugins that we&#8217;d like them to install, and some that are optional. Some people put them on, and some didn&#8217;t have time to read through and understand how to install them all in addition to understanding what they&#8217;re for and how to use them. To make that easier, we wanted to install all the plugins at once for them, and also make it a really simple to upgrade the main Eclipse installation.

We took a tip from the MyEclipse folks (no, we don&#8217;t use it), and setup a few directories as Externally Linked Features or [Product Extension][2]. So we setup a few directories like this on a shared drive:

<pre>stable-plugins/
    eclipse/
        features/
            first.feature_1.0.0/
            next.feature_1.0.0/
        plugins/
            first.feature_1.0.0/
            next.feature_1.0.0/
            first.plugin_1.0.0/
unstable-plugins/
    eclipse/
        features/
            trial.feature_1.0.0/
        plugins/
            trial.feature_1.0.0/
</pre>

And then on each developer&#8217;s machine, we create a place for them to put their own individual plugins.

<pre>user-plugins/
    eclipse/
        features/
        plugins/
            user.plugin_1.0.0/
</pre>

Finally, there&#8217;s just a few files and one directory to create in the main Eclipse installation on the developer&#8217;s machine.

<pre>eclipse/
    [...]
    links/
        stable.link
        unstable.link
        user.link
    [...]
</pre>

Each `.link` file contains the path to the directory above. For example, the `stable.link` file looks like this:

<pre>path=C:/path/to/stable-plugins
</pre>

Notice that it&#8217;s the path to the `stable-plugins` directory, and not to `stable/eclipse`. Eclipse expects to find the `eclipse` directory under the `path` pointed to in each `.link` file.

When we go to install a new plugin, we just make sure to choose which installation the plugin should go under. Remember that if you&#8217;re installing more than one plugin at a time, each one requires you to select the installation directory individually.

Select the plugin location for the first plugin&#8230;

![Eclipse plugin installation: Location chosen for first plugin][3]

&#8230;but the second plugin location has to be selected as well.

![Eclipse plugin installation: Location chosen for first plugin][4]

We can allow developers the freedom to disable any of the provided plugins, or even disable all the plugins for a particular extension location (like `unstable-plugins`). Simply go to `Help > Software Updates > Manage Configuration`. Click on the extension location, and then click `Disable` on the right.

![Ecplise Manage Configuration: Disable Extension Location][5]

We need to do one more thing before we can have a seamless upgrade of Eclipse from one version to the next: the workspace must not be in the Eclipse directory. We&#8217;ve setup our code similar to this:

<pre>work\
    company-repository\
        .metadata\
        project1\
        project2\
    other-code\
        .metadata\
        oss-project\
</pre>

We choose a standard place for the workspace to exist. Our source code repository ignores the `.metadata` directory, and all of our projects are located directly under the chosen workspace (`C:\work\company-repository`). This makes importing projects into the workspace easy, it keeps all of our code together, and it allows us to have a separate workspace for other code, such as open source software.

Now we&#8217;ve got a really great Eclipse configuration. We can share plugins amongst all of our developers in a standard way that ensures everyone has the right versions and such. Developers can choose to ignore unstable plugins, and they can add any plugins of their own. On top of that, there&#8217;s only one directory added to the standard Eclipse installation directory — the `links` directory. That means that it&#8217;s easy to upgrade to 3.1 or any milestone build. All you need to do is drop the `links` directory into the new installation, and you&#8217;re ready to go. When you open your new version of Eclipse, you&#8217;ll simply choose your existing workspace and all of your projects will appear, and your plugins will be installed (assuming they work with the new version).

Anyone who tried to keep up with the moving milestones of 3.0 can appreciate how easy this configuration is to upgrade frequently, and if you&#8217;re looking for a way to standardize the Eclipse plugins used in a corporate environment this just might work for you. If you&#8217;ve got improvements to this setup, I&#8217;d really love to hear them!

 [1]: http://www.eclipse.org/ "Eclipse Java IDE"
 [2]: http://help.eclipse.org/help30/index.jsp?topic=/org.eclipse.platform.doc.isv/guide/product_extension.htm "Eclipse 3.0 Help: Product Extensions"
 [3]: /blog/files/pluginlocationchosen.gif
 [4]: /blog/files/pluginlocationnotchosen.gif
 [5]: /blog/files/disableplugins.gif
