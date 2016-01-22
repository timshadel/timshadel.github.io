---
title: Extracting CAS configuration into YAML, like database.yml
author: Tim
layout: post
permalink: /2008/05/31/extracting-cas-configuration-into-yaml-like-databaseyml/
categories:
  - How-To
tags:
  - authentication
  - cas
  - rails
  - ruby
  - rubycas-client
  - yaml
---
If you&#8217;ve done any enterprise work with Rails, and your shop is using [CAS][1] for authentication, chances are you&#8217;ve seen [rubycas-client][2]. Chances are you&#8217;ve also loved how easy it was to get working. There&#8217;s usually only one hitch &#8212; you&#8217;ve got to change the config based on which environment you&#8217;re deploying into.

Here&#8217;s the standard advice you get from the RDoc:

{% highlight ruby %}
# in your config/environment.rb
CASClient::Frameworks::Rails::Filter.configure(
  :cas_base_url => "https://cas.example.foo/",
  :proxy_retrieval_url => "https://cas-proxy-callback.example.foo/cas_proxy_callback/retrieve_pgt",
  :proxy_callback_url => "https://cas-proxy-callback.example.foo/cas_proxy_callback/receive_pgt",
  :logger => cas_logger
)
{% endhighlight %}


<!--more-->

But with a tiny change, you can give your CAS setup all the flexibility and auto-magical environmental savvy of `database.yml`. Goodbye last minute edits for a production deployment. Check this out:

{% highlight ruby %}
# in your config/environment.rb
cas_options = YAML::load_file(RAILS_ROOT+'/config/cas.yml')
CASClient::Frameworks::Rails::Filter.configure(cas_options[RAILS_ENV])
{% endhighlight %}

Now make a simple YAML file, `cas.yml`:

{% highlight yaml %}
# config/cas.yml
development:
    :cas_base_url: https://cas.qaexample.tld/cas/
    :validate_url: https://cas.qaexample.tld/cas/validate
    :logout_url: https://cas.qaexample.tld/cas/logout


test:
    :cas_base_url: https://cas.qaexample.tld/cas/
    :validate_url: https://cas.qaexample.tld/cas/validate
    :logout_url: https://cas.qaexample.tld/cas/logout



production:
    :cas_base_url: https://cas.example.tld/cas/
    :validate_url: https://cas.example.tld/cas/validate
    :logout_url: https://cas.example.tld/cas/logout
{% endhighlight %}

It&#8217;s worth noting that the colons in front of the YAML keys indicate that those keys are Ruby symbols, not strings.  All the rubycas-client docs use symbols in their examples, so I&#8217;d follow their lead if I were you.

Got an opinion about using CAS with Rails?  Leave a comment and let us hear it!

 [1]: http://www.ja-sig.org/products/cas/
 [2]: http://rubycas-client.rubyforge.org/
