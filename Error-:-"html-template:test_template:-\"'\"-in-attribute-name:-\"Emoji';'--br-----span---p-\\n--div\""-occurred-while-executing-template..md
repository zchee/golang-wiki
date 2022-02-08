I am using "html/template" package, while try to execute the template by using t.Execute(wr io.Writer, data interface{}) function error return : `Error : "html/template:test_template: \"'\" in attribute name: \"Emoji';'><br /></span></p>\\n</div\""`.

template content is given below:

``<p style="font-family: Lato, sans-serif, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, 'Noto Sans', 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';">test</p>``