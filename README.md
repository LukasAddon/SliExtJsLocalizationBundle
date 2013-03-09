Introduction
------------
Bundle adds translation support of ExtJs classes to Symfony2.


Prerequisites
-------------
In order the task to detect your extjs class it must comply with the following rules:
- Before the very first translation token this comment must be placed - // l10n
- Translation tokens must be suffixed with "Text", for example - firstnameText
- One blank line must follow after translation tokens and other class members ( other properties, methods etc )
- Do not add any blank lines between translation tokens ( you might be tempted to do this to group your tokens semantically )

See for Tests/*/resources for examples of valid extjs classes.

Usage
-----
Most of the time all you need to do in order to start translating your project's extjs classes is to execute
the following command:

``` bash
php app/console sli:update-extjs-translation fr AcmeDemoBundle --output-format=xlf
```

After executing the command, given that you have AcmeDemoBundle installed in your project and the bundle has 
"Resources/public/js/" directory ( and some classes inside it ), then the command will parse the files inside
this directory and generate Resources/translations/extjs.fr.xlf file.

Once you have some translation catalogues in place, in your templates you can use either this:

``` twig
<script type="text/javascript" src="{{ path('sli_extjs_route', { locale: 'fr' }) }}"></script>
```

or this:

``` twig
<script type="text/javascript">
  {{ render(url('sli_extjs_route', { locale: 'fr' })) }}}
</script>
```

to have them loaded. The only difference between these two examples is that in the second one, the generated by bundle
javascript code will be embedded rith in the template.


Configuration
-------------

If you need to change URL that is used to generate extjs-localization code then you can override value of "sli_ext_js_localization.route" 
service container configuration parameter. 