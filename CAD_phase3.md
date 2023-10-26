**PROJECT: PERSONAL BLOG WITH IBM CLOUD STATIC WEB APPS**

DEVELOPMENT PART

In the development phase of "Personal Blog", design a user-friendly HTML/CSS . Extensive testing, potential user authentication with help of  static site generator  Hugo to make it easy to update and manage the blog content. This would involve converting your HTML content into template files that can be easily updated and deployment on IBM Cloud prepare the blog for production use.

CONTENT PLANNING :

My personal blog(Home)

About

Contect

Code :

**Download the pre-built Hugo executable for Windows**

1. Open [https://github.com/spf13/hugo/releases 727](https://github.com/spf13/hugo/releases) in your browser.
2. The current version is hugo\_0.12\_windows\_amd64.zip.
3. Download that ZIP file and save it in your D:\Hugo\bin folder.
4. Find that ZIP file in Windows Explorer and extract all the files from it.
5. You should see a .exe file with the same name as the ZIP file.
6. Rename that .exe file to hugo.exe.
7. Verify that the hugo.exe file is in the D:\Hugo\bin folder. (It’s possible that the extract put it in a sub-directory. If it did, use Windows Explorer to move it to D:\Hugo\bin.)


**Generate your first site**

Open a command prompt window.

At the prompt, change your directory to the Sites directory.

C:\Program Files> cd D:\Hugo\Sites

C:\Program Files> D:

D:\Hugo\Sites>

Run the command to generate a new site. I’m using example.com as the name of the site.

D:\Hugo\Sites> D:\Hugo\bin\hugo new site example.com

Note that you must type the full path to hugo unless you’ve updated your system PATH variable!

4\. You should get output similar to the following: TODO: grab output and put here

You now have Hugo installed and a site to work with. You need to add a layout (or theme), then create some content. Go to http://gohugo.io/overview/quickstart/ 302 for steps on doing that.


![hugo_menu](https://github.com/Vasanthv7/Personal-Blog/assets/126228661/a285680b-257c-45c0-a550-61ec7e28c08a)



Code:

Default.md

+++

title = '{{ replace .File.ContentBaseName "-" " " | title }}'

date = {{ .Date }}

draft = true

+++

Downlod themes :

 By using git clone method to clone the git repo

  git clone https//git.com/<repo\_name>/ themes/paper

![theme](https://github.com/santhoshkumarr1214/Personal-Blog/assets/144305419/132cca78-0424-4781-a557-0aad2f78af89)


Configure hugo.toml

baseURL = 'https://example.org/'

languageCode = 'en-us'

title = 'My personal blog'

theme = "paper"

disqusshortname=""

paginate = 6

disqusShortname = 'YOUR\_DISQUS\_SHORTNAME'   # use disqus comments


[params]

  # color style

  color = 'linen'                           # linen, wheat, gray, light

  cover = "img/blog1.png"

  # header social icons

  twitter = 'YOUR\_TWITTER\_ID'               # twitter.com/YOUR\_TWITTER\_ID

  github = 'vasanthv7'                      # github.com/vasanthv7

instagram = 'YOUR\_INSTAGRAM\_ID'           # instagram.com/YOUR\_INSTAGRAM\_ID

linkedin = 'Vasanth B'             # linkedin.com/in/Vasanth B



# home page profile

 avatar = 'GRAVATAR\_EMAIL'                 # gravatar email or image url

 name = 'blogger'

 bio = 'Always say yes to new adventures'

 [menu]

[[menu.main]]

 identifier = "about"

name = "About"

url = "/about/"

weight = 10

 [[menu.main]]

 identifier = "contact"

 name = "Contact"

 url = "/contact/"

 weight = 10

**layouts>>\_default>>baseof.html**

![default](https://github.com/santhoshkumarr1214/Personal-Blog/assets/144305419/a4335bc5-3b6b-4fb5-bf77-97a954768d39)




<!doctype html>

{{ $.Scratch.Delete "bg\_color" }}<!---->

{{ $.Scratch.Delete "social\_list" }}<!---->

{{ $.Scratch.Delete "avatar\_url" }}<!---->

<!-- bg\_color -->

{{ $color\_map := dict "linen" "#faf8f1" "wheat" "#f8f5d7" "gray" "#fbfbfb"

"light" "#fff" }}<!---->

{{ $.Scratch.Set "bg\_color" (index $color\_map (site.Params.color | default

(print "linen"))) }}<!---->

{{ $bg\_color := $.Scratch.Get "bg\_color" }}<!---->

<!-- social\_list -->

{{ $social\_params := slice "twitter" "github" "instagram" "linkedin" 

` `}}<!---->

{{ range $social\_params }}<!---->

{{ if isset site.Params . }}<!---->

{{ $.Scratch.Add "social\_list" (slice .) }}<!---->

{{ end }}<!---->

{{ end }}<!---->

<!-- avatar\_url -->

{{ if site.Params.avatar }}<!---->

{{ if in site.Params.avatar "http" }}<!---->

{{ $.Scratch.Set "avatar\_url" site.Params.avatar }}<!---->

{{ else }}<!---->

{{ $official\_cdn := "https://www.gravatar.com/avatar/" }}<!---->

{{ $cdn := (site.Params.gravatarCdn | default $official\_cdn) }}<!---->

{{ $md5 := (md5 site.Params.avatar) }}<!---->

{{ $avatar\_url := print $cdn $md5 "?s=160&d=identicon" }}<!---->

{{ $.Scratch.Set "avatar\_url" $avatar\_url }}<!---->

{{ end }}<!---->

{{ end }}<!---->

<html

 class="not-ready lg:text-base"

 style="--bg: {{ $bg\_color }}"

`lang="{{ or site.LanguageCode site.Language.Lang }}"

\>

{{ partial "head.html" . }}

<body class="text-black duration-200 ease-out dark:text-white">

 {{ partial "header.html" . }}

<main

class="prose prose-neutral relative mx-auto min-h-[calc(100%-9rem)] max-w-3xl px-8 pb-16 pt-12 dark:prose-invert"

>

 {{ block "main" . }}



 {{ end }}

  </main>

  {{ partial "footer.html" . }}

 </body>

</html>

**layouts>>\_default>>list.html**

{{ define "main" }}

<!-- Tag Title -->

{{ if and .Title (eq .Type "tags") }}

<h1 class="mb-16">#{{ .Title }}</h1>

{{ end }}

<!-- $pages -->

{{ $pages := union .RegularPages .Sections }}<!---->

{{ if .IsHome }}<!----><img src="img/blog1.png" width="800" height="60">

{{ $pages = where site.RegularPages "Type" "in" site.Params.mainSections }}<!---->

{{ end }}

<!-- Articles -->

{{ $paginator := .Paginate $pages }} {{ range $index, $page := $paginator.Pages

}}<!---->


<!-- avatar -->

{{ if and $.IsHome (eq $paginator.PageNumber 1) (eq $index 0) }}<!---->

{{ $avatar\_url := $.Scratch.Get "avatar\_url" }}<!---->

{{ if or $avatar\_url site.Params.name }}

<div class="-mt-2 mb-16 flex items-center">

  {{ if $avatar\_url }}

  <div

 class="mr-5 shrink-0 rounded-full border-[0.5px] border-black/10 bg-white/50 p-3 shadow dark:bg-white/[15%]"

>

 <img

 class="my-0 aspect-square w-16 rounded-full !bg-black/5 hover:animate-spin dark:!bg-black/80"

 src="{{ $avatar\_url }}"

 alt="{{ site.Params.name | default site.Title }}"

 />

 </div>

 {{ end }}<!---->

{{ if site.Params.name }}

<div>

 <h1 class="mb-2 mt-3 text-[1.6rem] font-bold">{{ site.Params.name }}</h1>

 <div class="break-words">

 {{ site.Params.bio | default (print `A personal blog by `

 site.Params.name) }}

 </div>

</div>

{{ end }}

</div>

{{ end }}<!---->

{{ end }}

<section class="relative my-10 first-of-type:mt-0 last-of-type:mb-0">

{{ if gt .Weight 0 }}

<span

class="mb-2 ml-px inline-block text-[0.8rem] font-medium uppercase tracking-wider text-[#ff3b2d] opacity-70"

>Featured</span

>

{{ end }}

<h2 class="!my-0 pb-1 font-bold !leading-none">{{ .Title }}</h2>

<time class="text-sm antialiased opacity-60"

 >{{ .Date | time.Format ":date\_medium" }}</time

>

<a class="absolute inset-0 text-[0]" href="{{ .Permalink }}">{{ .Title }}</a>

</section>

{{ end }}

<!-- Main Nav -->

{{ if gt $paginator.TotalPages 1 }}

<nav class="mt-16 flex">

 {{ if $paginator.HasPrev }}

 <a class="btn" href="{{ $paginator.Prev.URL }}">← {{ i18n "prev\_page" }}</a>
 {{ end }}<!---->

 {{ if $paginator.HasNext }}

 <a class="btn ml-auto" href="{{ $paginator.Next.URL }}"

 >{{ i18n "next\_page" }} →</a

 >

{{ end }}

</nav>

{{ end }}<!---->

{{ end }}

**layouts>>\_default>>single.html**


{{ define "main" }}

<article>

<header class="mb-16">

 <h1 class="!my-0 pb-2.5">{{ .Title }}</h1>

 {{ if ne .Type "page" }}

 <div class="text-sm antialiased opacity-60">

 {{ if .Date }}

 <time>{{ .Date | time.Format ":date\_medium" }}</time>

 {{ end }}<!---->

 {{ $single\_author := or .Params.Author site.Author.name }}

 <!---->

 {{ if $single\_author }}

<span class="mx-1">&middot;</span>

 <span>{{ $single\_author }}</span>

 {{ end }}

 </div>

 {{ end }}

 </header>

 <section>{{ .Content }}</section>

 <!-- Post Tags -->

 {{ if .Params.tags }}

 <footer class="mt-12 flex flex-wrap">

 {{ range .Params.tags }} {{ $href := print (absURL "tags/") (urlize .) }}

 <a

 class="mb-1.5 mr-1.5 rounded-lg bg-black/[3%] px-5 py-1.5 no-underline dark:bg-white/[8%]"

 href="{{ $href }}"

>{{ . }}</a

>

{{ end }}
</footer>

{{ end }}

<!-- Post Nav -->

{{ if not site.Params.disablePostNavigation }}<!---->

{{ $pages := where site.RegularPages "Type" "in" site.Params.mainSections }}<!---->

{{ if and (gt (len $pages) 1) (in $pages . ) }}

<nav class="mt-24 flex rounded-lg bg-black/[3%] text-lg dark:bg-white/[8%]">

{{ with $pages.Next . }}

<a

class="flex w-1/2 items-center rounded-l-md p-6 pr-3 font-semibold no-underline hover:bg-black/[2%] dark:hover:bg-white/[3%]"

href="{{ .Permalink }}"

><span class="mr-1.5">←</span><span>{{ .Name }}</span></a

>

{{ end }}<!---->

{{ with $pages.Prev . }}

<a

  class="ml-auto flex w-1/2 items-center justify-end rounded-r-md p-6 pl-3 font-semibold no-underline hover:bg-black/[2%] dark:hover:bg-white/[3%]"

     href="{{ .Permalink }}"

   ><span>{{ .Name }}</span><span class="ml-1.5">→</span></a

 >

 {{ end }}

 </nav>

 {{ end }}<!---->

 {{ end }}<!---->

 <div class="con1">      

<!-- Disqus -->

  {{ if and site.DisqusShortname (not (eq .Params.comments false)) }}<!--

   <div class="mt-24" id="disqus\_thread"></div>

  <script>

   const disqusShortname = '{{ site.DisqusShortname }}';

   const script = document.createElement('script');

  script.src = 'https://' + disqusShortname + '.disqus.com/embed.js';

   script.setAttribute('data-timestamp', +new Date());

   document.head.appendChild(script);
   </script>-->

   <div id="disqus\_thread"></div>

   <script>

   /\*\*

https://disqus.com/admin/universalcode/#configuration-variables    \*/

  \*

  var disqus\_config = function () {

  this.page.url = PAGE\_URL;  // Replace PAGE\_URL with your page's canonical URL variable

  this.page.identifier = PAGE\_IDENTIFIER; // Replace PAGE\_IDENTIFIER with your page's unique identifier variable

   };

\*/

(function() { // DON'T EDIT BELOW THIS LINE

var d = document, s = d.createElement('script');
s.src = 'https://personal-bolg.disqus.com/embed.js';

s.setAttribute('data-timestamp', +new Date());

(d.head || d.body).appendChild(s);

})();

</script>

<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref\_noscript">comments powered by Disqus.</a></noscript>

<script id="dsq-count-scr" src="//personal-bolg.disqus.com/count.js" async></script> {{ end }}

</div>

<style> 

.con1 {

`margin-top: 20px; /\* Add space below content 1 \*/

}

</style>

{{ if and site.DisqusShortname (not (eq .Params.map1 false)) }}

<div class="mapouter"><div class="gmap\_canvas"><iframe width="752" height="500" id="gmap\_canvas" src="https://maps.google.com/maps?q=big%20temple%20thanjavur&t=&z=13&ie=UTF8&iwloc=&output=embed" frameborder="0" scrolling="no" marginheight="0" marginwidth="0"></iframe><a href="https://123movies-i.net">american psycho 123movies</a><br><style>.mapouter{position:relative;text-align:right;height:500px;width:752px;}</style><a href="https://www.embedgooglemap.net"></a>

<style>.gmap\_canvas {overflow:hidden;background:none!important;height:500px;width:752px;}</style></div></div>

{{end}}

`  `<div class="mapt">

`    `{{ if and site.DisqusShortname (not (eq .Params.map2 false)) }}

`    `<div class="mapouter"><div class="gmap\_canvas"><iframe width="1080" height="500" id="gmap\_canvas" src="https://maps.google.com/maps?q=tourist%20place%20in%20delhi&t=&z=15&ie=UTF8&iwloc=&output=embed" frameborder="0" scrolling="no" marginheight="0" marginwidth="0"></iframe><a href="https://123movies-i.net">american psycho 123movies</a><br><style>.mapouter{position:relative;text-align:right;height:500px;width:1080px;}</style><a href="https://www.embedgooglemap.net"></a>

`<style>.gmap\_canvas {overflow:hidden;background:none!important;height:500px;width:1080px;}</style></div></div>

{{end}}

</div>

`<style>

.mapt{

`    `width: 100%; /\* Set the width of the map to 100% of its container \*/

` `/\* Set the height of the map as needed \*/

margin: 0 auto; /\* Center horizontally \*/

text-align: center;

}

</style>  

</article>

{{ end }}

**Partials**

![partials](https://github.com/Vasanthv7/Personal-Blog/assets/126228661/714443f2-cbcd-4308-ad51-a8839d871b7a)


**Partials>>footer.html**

<footer

class="opaco mx-auto flex h-[4.5rem] max-w-3xl items-center px-8 text-[0.9em] opacity-60"

\>

<div class="mr-auto">

&copy; {{ now.Year }}

<a class="link" href="{{ `` | absURL }}">{{ site.Title }}</a>

</div>

<a class="link mx-6" href="https://gohugo.io/" rel="noopener" target="\_blank"

>Powered by Hugo️️</a

>️

<a

class="link"

href="https://github.com/nanxiaobei/hugo-paper"

rel="noopener"

target="\_blank"

>✎ Paper</a

>

</footer>

**Partials>>header.html**

<header class="mx-auto flex h-[4.5rem] max-w-3xl px-8 lg:justify-center">

<div class="relative z-50 mr-auto flex items-center">

<a

class="-translate-x-[1px] -translate-y-[1px] text-2xl font-semibold"

href="{{ `` | absURL }}"

>{{ site.Title }}</a

>

<div

class="btn-dark text-[0] ml-4 h-6 w-6 shrink-0 cursor-pointer {{ if site.Params.monoDarkIcon }}[background:url(./theme.svg)\_left\_center/cover\_no-repeat] dark:invert{{ else }}[background:url(./theme.png)\_left\_center/\_auto\_theme('spacing.6')\_no-repeat] [transition:\_background-position\_0.4s\_steps(5)]{{ end }} dark:[background-position:right]"

role="button"

aria-label="Dark"

></div>

</div>

<div

class="btn-menu relative z-50 -mr-8 flex h-[4.5rem] w-[5rem] shrink-0 cursor-pointer flex-col items-center justify-center gap-2.5 lg:hidden"

role="button"

aria-label="Menu"

></div>

{{ $bg\_color := $.Scratch.Get "bg\_color" }}<!---->

<script>

// base

const htmlClass = document.documentElement.classList;

setTimeout(() => {

htmlClass.remove('not-ready');

`}, 10);

const btnMenu = document.querySelector('.btn-menu');

btnMenu.addEventListener('click', () => {

htmlClass.toggle('open');


};

// init

const darkScheme = window.matchMedia('(prefers-color-scheme: dark)');

if (htmlClass.contains('dark')) {

setDark(true);

} else {

const darkVal = localStorage.getItem('dark');

setDark(darkVal ? darkVal === 'true' : darkScheme.matches);

}

darkScheme.addEventListener('change', (event) => {

setDark(event.matches);

});
// manual switch

const btnDark = document.querySelector('.btn-dark');

btnDark.addEventListener('click', () => {

setDark(localStorage.getItem('dark') !== 'true');

});

</script>

<div

class="nav-wrapper fixed inset-x-0 top-full z-40 flex h-full select-none flex-col justify-center pb-16 duration-200 dark:bg-black lg:static lg:h-auto lg:flex-row lg:!bg-transparent lg:pb-0 lg:transition-none"

>

{ $url := .RelPermalink }}<!---->

{{ with site.Menus.main }}

<nav class="lg:ml-12 lg:flex lg:flex-row lg:items-center lg:space-x-6">

{{ range . }}

<a

class="block text-center text-2xl leading-[5rem] lg:text-base lg:font-normal"

href="{{ .URL }}"

>{{ .Name }}</a

`>

{{ end }}

</nav>

{{ end }}<!---->

`{{ with $.Scratch.Get "social\_list" }}

`<nav

class="mt-12 flex justify-center space-x-10 dark:invert lg:ml-12 lg:mt-0 lg:items-center lg:space-x-6"

>

{{ range . }}<!---->

<a

class="h-8 w-8 text-[0] [background:var(--url)\_center\_center/cover\_no-repeat] lg:h-6 lg:w-6"

`style="--url: url(./{{ . }}.svg)"

href="{{ if eq . `rss` }}{{ `index.xml` | absURL }}{{ else if eq . `mastodon` }}{{ index site.Params . }}{{ else }}https://{{ . }}.com/{{ if eq . `linkedin` }}in/{{ end }}{{ index site.Params . }}{{ end }}"

target="\_blank"

rel="{{ if eq . `rss` }}alternate{{ else }}me{{ end }}"

>

{{ . }}

</a>

{{ end }}<!---->

</nav>

{{ end }}<!---->

</div>

</header>

**Output**

**Dark mode**


![main page](https://github.com/santhoshkumarr1214/Personal-Blog/assets/144305419/f71dc023-724a-411c-b2a1-2d27a30ec3e5)

In normal 

![dark](https://github.com/santhoshkumarr1214/Personal-Blog/assets/144305419/41684ae1-445c-45ed-bd68-fa513f80a88a)


Interactive Comment section 


![comment](https://github.com/santhoshkumarr1214/Personal-Blog/assets/144305419/a62603e2-d926-4163-a4cb-5fe5d23452a2)

Interactive map (for each blog)

![map](https://github.com/santhoshkumarr1214/Personal-Blog/assets/144305419/8f57b775-1bfe-4382-81d5-d09e3d90f5a5)


Conclution:

In this part you will begin building your project. Start by designing and developing the static travel blog website. Design the website layout using HTML and CSS. Create engaging content with captivating photos and travel stories. 




