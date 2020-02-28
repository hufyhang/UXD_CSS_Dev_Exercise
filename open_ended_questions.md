## What are some best practices for ensuring proper accessibility support?

From my very humble point of view, ensuring proper accessibility support is a two-fold effort. It requires to be pursuit by designers and front-end developers together.

As a designer, the effort should be spent on, for example, (1) ensuring the color (foreground and background) used match the WCAG's level AA and/or AAA; (2) using appropriate font size on text contents for all the target devices (e.g. desktops, phones, tablets); (3) ensuring elements can be easily described/narrative by text when using images to present information to users.

As a developer, beside implementing web pages designed by designers, additional efforts should be spent on, for example, (1) making proper use of "aria" attributes to enhance the accessibility of the elements present on web page; (2) ensuing the use of "alt" attribute on images; (3) making use of proper semantic tags/directives (e.g. nav, main, section) according to the nature of each elements.

Additionally, some front-end frameworks do provide decent accessibility enhancing features. They can, for instance, "automatically" apply proper "aria" attributes and even wrapping DOM/HTML elements to particular elements/nodes for developers to facilitate the use of these accessibility ensuring/enhancing techniques.

Once a web page is developed, front-end developers may also rely on screen readers to confirm/double check if the structure and all the important information are correctly delivered to the users who have seeing issues.

Moreover, there are several browser plugins/extensions available to help us check the accessibility of each web page. For the one that I used during my previous employment, it checks, for example, (1) if the web page matches AA/AAA; (2) if the semantics/DOM structure is decent; (3) if all the roles (including "aria-role") are appropriate.

All in all, the above are the practices that I used/known to enhance accessibility support.


## How do you test to ensure your development work matches the design you are provided?

Normally, once my development work is finished, I ask designer(s) to join me to check if the work matches the design. Besides that, in my early working experience, we also made attempts to applying some automatic approaches/techniques to make the checks. For example, we attempted to apply "screenshot-comparing" technologies that typically used in regression testings to do the job. Basically, we use the design outputs (in the form of images) as the baseline of the tests, and then take screenshots for the development work. The comparing tool/script will then automatically identify the visual differences it detected on the screenshot. From my own experience, it did take some extra efforts to make the whole approach works properly, however, once it is all set, the life becomes much easier. :-)

Also, there was a browser extension (not sure if it is still available) which does more or less the same as the approach I described above. It allows developer to set the design image as the background layer of the web page, then developers will see if there is any visual differences on the development work.



## What are some best practices for ensuring cross-browser compatibility?

First off, it is important to make sure what browsers are to be supported by the project/product. Usually, when a project is required to support, for example, legacy IEs, we have to be careful with the techniques (HTML, CSS, and JavaScript) that we used for implementations.

Generally, for HTML, make sure to use proper and standard HTML elements. It might not be a good idea to use the ones that are either deprecated or only available for very specific browsers. If we are unsure which HTML elements are standard or have decent browser support, we can normally refer to Mozilla Developer Network (MDN)'s documentations. So far as I know, Microsoft/IE has also provided documentations and some developers may rely on them rather than MDN. However, according to my very own experience, Microsoft's documentation is more dedicated to IE as there might be some differences with the ones that widely applied/followed by other venders. Thus, my humble suggestion is to stick with MDN's, always. :-)

Moreover, make sure all the web pages have proper "DOCTYPE" statements. Otherwise, the browsers will kick off quirk mode to render web pages.

Additionally, HTML5 is nowadays very well supported by modern browsers. However, some legacy IEs do not recognize HTML5 tags. In this case, we can rely on libraries such as "html5shiv" to help us make use of HTML5 tags in those browsers.

For CSS, pretty much the same as the situation in "HTML", stay with MDN documentations for CSS to see which rules are well supported. Also, there are some tools that can help to exam the compatibility of the stylesheets that we authored. For example, [doiuse](https://www.npmjs.com/package/doiuse) is one of the most adopted tools to automatically check CSS compatibility in stylesheets.

Plus, remember to use vender prefixes (e.g. -webkit-XXX, -ms-XXX) for certain rules. It is, at least for me, a bit challenging to memorize all the ones require vender prefixes. So that tools like [autoprefixer](https://www.npmjs.com/package/autoprefixer) is something that can be used.

Further more, if it is allowed, some widely used libraries/frameworks, such as Bootstrap, can be really helpful since they spent a significant amount of efforts to ensure cross-browser compatibility.

One more last thing I would like to share for CSS is the importance of "CSS resetting". Basically, each browser equips several initial/UA styles for different HTML elements by default. Since these styles are from different vendors, the styles could be different across browsers. Therefore, it is an additional good and common practice to "reset" these initial styles before authoring particular stylesheets. This can be done by either import some widely used 3rd-party libraries such as "Eric Meyer CSS Reset", or write a specific reset stylesheet dedicated to the projects/products by ourself. Notice that "box-sizing" (which tells browsers how the dimension of a box is calculated) could also treated as an additional rule to be reset.

For JavaScript, again, it is a good idea to refer to MDN's docs. Moreover, a good coding style can be critical in ensuring JS compatibility. A short story I would like to share is that during my previous working experience, a colleague of mine came to seek my help for debugging a piece of JS (in CoffeeScript, actually) he wrote. The function works correctly on most browsers except a particular one. All the logics were correct in his code. By the end, we realized that his code is incorrectly interpreted by CoffeeScript compiler for that browser (the company used different versions of compilers for desktop and mobile releases). Moreover, we realized that it could be actually avoid if he follow our coding style guidelines strictly.

Also, JSlint/ESlint is the tool that we heavily relied on to ensure a good coding style for better compatibility (linters can also help to avoid some other issues).

Finally, for testing, even though we have loads of tools and guides to help us ensure compatibility, it is still a good idea to test the development works on real browsers. Indeed, the cost sometimes can be expensive as it may requires a large number of devices, there are some paid service, such as BrowserStack, to help us test our works on different browsers. If there are sufficient resources locally, BrowserSync can save us time to kick off tests on different setups.



## Have you used any design systems, if so which ones?

When I was in Oracle, we used Oracle JET as the framework for front-end development. I was told that there was a corresponding design system available for designers. From my understanding, a design system helps designer/designs and developers/development outcomes always stay on the same page. In short, they share the same stylings (including spacing, font styles, color, etc.) between each other to ensure developers can easily deliver the exactly same web pages as designers designed.

In my first employment, we also attempted to develop and maintain, I envisage, a design system of our own. The approach might be clumsy, but we first identified and designed all the possible elements (including spacings, colors, font styles, buttons, forms, etc.) can be used in our product in the form of a spec-like asset that can be utilized by designers, and then, as the front-end developers, we implemented all these elements in the form of a library (like what Bootstrap does) that can be easily utilized by developers. Once a particular design spec is required to be modified, we will also change the previous implementation of the particular element in the front-end library to reflect the changes.

As a result, it not only made sure the design and development works were always same, but also helped designers and developers to easily stay on the same page by filling some gaps between us.




## What are some pros and cons to working with a design system?

I guess I have already talked about the pros of working with a design system in my answers to the previous question. :-) For short, it helps designers and developers to stay on the same page by filling some cognitive gaps between them, and facilitate the delivery of the same result of design and development.

For the cons, I suppose the first thing come through my mind is that the implementation and maintenance of a design system can be, sometimes, costly. From my experience, if the work is started from scratch, designers and developers have to identify and summarize all the elements that will be possibly used in products. Once such a system is developed, efforts have to be spent on applying it to all the existing designs and codes that were done without the design system. This could be quite expensive since depending on the scale of the existing assets, a large number of regression tests have to be made. After that, when something changed in the design system later on, additional regression tests and reviews may also required to be conducted.

Secondly, a design system sometimes is like a guideline or even a strict rule to be followed by designers and developers, it could possibly limit the way of designing new elements/web pages. From the perspective of creativity, it may more or less limit the freedom of creating new things. :-)




## What are some features you’d like to see added to the CSS/HTML specs?

Without considering the difficulties of implementing the features, the very first thing I would love to add to CSS spec is "nested selectors" in vanilla CSS. Nested Selector is one of the most used features that I used in pre-compiling languages, such as Stylus, Post CSS. For me, it not only simplifies the authoring of selectors, but also brings us ability to organize selectors and styling rules. For example, we can write something like below in Stylus:

```stylus
.parent
   color: red

   .children
      color: grey

     .grand-children
       color: blue
```

However, in vanilla CSS so far, we have to do things in the way below:

```css
.parent {
  color: red;
}

.parent .children {
  color: grey;
}

.parent .children .grand-children {
  color: blue;
}
```

Another feature I would to see in CSS spec (again, without worrying about the technical difficulties) is "backward selector". For instance, if we want to modify the style of the parent of a particular element (e.g. being hovered), we nowadays may rely on JavaScript to handle the mouse event of the child element to append, for example, an extra class to its parent node. However, with "backward selector", it can be easily achieved in vanilla CSS in the below way:

```css
.target:hover(<< body) {
  background: yellow;
}
```



## In your career to-date what are you most proud of?

Most of my major achievements in my working experience to-date are already presented in my CV, hence I would love to share another story which made me most prod of in my career. The reason it is not on my CV is that the "story" was classified for my former employer. I just confirmed with my former boss, since they already stopped doing that related business, I am allowed to tell the story now. :-)

Long story short, during my first employment a significant number of time and efforts of ours were spent on handling and implementing the customized business processes required and defined by our customers. However, we later on realized that most of the processes were actually more or less the same/similar. Hence, after reviewing all the scheduled tasks by hand, I talked with the CTO to see if there is any chance for me/us to do something to save our time and costs. As a result, CTO and I (as the lead of front-end development) decided to kick off a project called "reusable business patterns"(RBP) to abstract all the common and reusable business processes into separated functions in front-end JavaScript and back-end Python. By feeding the customized configurations from different customers, our product can then automatically assemble the desired business process to fulfill the requirements from our clients.

The whole RBP project took us over two months to get all things done. The result was promising. I myself was quite proud of the efforts that I spent on this particular project because it was not only one of the great achievement we, the dev team, made, but also, more importantly, saved a significant number of resources (time, money, and human resources) for my company in future.


