## 0. January 17, 2024

### 0. To move the original homepage to `/blog` and add the link to new page in navbar:

1. **Creating the page layout:** Copy the entire code from `./layouts/index.html` to `./layouts/section/blog.html`
2. **Add navbar link:** Add blog entry to `./layouts/partials/navigation.html` as
``` html
<a href="{{ "/blog" | relURL }}">{{ with .Site.Params.blog }}{{ . }}{{ else }}{{ i18n "blog" }}{{ end }}</a>
```
3. **Usage:** The website using this theme should also have a `./content/blog/_index.md` file (empty file works)
4. **Language translations:** Add required langauge transaltions to to `/i18n`

### 1. To replace homepage with About
1. **Remove navbar link:** Remove link to `About` from `./layouts/partials/navigation.html`
2. **Import content to homepage:** In `./layouts/index.html`, replace old content with the following:
```html
{{ define "main" }} {{ partial "profile.html" . }}
<section id="section">
  {{with .GetPage `about/_index.md`}} {{.Content}} {{end}}
</section>
{{ end }}
```
Thank you [StackOverflow](https://stackoverflow.com/questions/74247325/change-the-main-landing-page-of-my-hugo-blog) and [documentation](https://gohugo.io/methods/page/getpage/)

3. **Cleanup:** Delete `layouts/section/about.html`
