# About React and Next.js

Next.js is a flexible React framework that gives you building blocks to create fast, full-stack web applications.

But what exactly do we mean by this? Let's spend some time expanding on what React and Next.js are and how they can help you build web applications.

Building blocks of a web application
There are a few things you need to consider when building modern applications. Such as:

## User Interface - how users will consume and interact with your application.
## Routing - how users navigate between different parts of your application.
## Data Fetching - where your data lives and how to get it.
## Rendering - when and where you render static or dynamic content.
## Integrations - what third-party services you use (for CMS, auth, payments, etc.) and how you connect to them.
## Infrastructure - where you deploy, store, and run your application code (serverless, CDN, edge, etc.).
## Performance - how to optimize your application for end-users.
## Scalability - how your application adapts as your team, data, and traffic grow.
## Developer Experience - your team's experience building and maintaining your application.
For each part of your application, you will need to decide whether you will build a solution yourself or use other tools, such as packages, libraries, and frameworks.

## What is React?
React is a JavaScript library for building interactive user interfaces.

By user interfaces (UI), we mean the elements that users see and interact with on-screen.

User Interface example showing a browser window with a navigation, a sidebar, and a list of posts
By library, we mean React provides helpful functions (APIs) to build UI, but leaves it up to the developer where to use those functions in their application.

Part of React's success is that it is relatively unopinionated about the other aspects of building applications. This has resulted in a flourishing ecosystem of third-party tools and solutions, including Next.js.

It also means, however, that building a complete React application from the ground up requires some effort. Developers need to spend time configuring tools and reinventing solutions for common application requirements.

## What is Next.js?
Next.js is a React framework that gives you building blocks to create web applications.

By framework, we mean Next.js handles the tooling and configuration needed for React, and provides additional structure, features, and optimizations for your application.


The browser then reads the HTML and constructs the Document Object Model (DOM).

# What is the DOM?
The DOM is an object representation of the HTML elements. It acts as a bridge between your code and the user interface, and has a tree-like structure with parent and child relationships.

Two side-by-side diagrams, left showing the DOM tree, and right showing the rendered UI.
![alt text](image.png)

You can use DOM methods and JavaScript, to listen to user events and manipulate the DOM by selecting, adding, updating, and deleting specific elements in the user interface. DOM manipulation allows you to not only target specific elements, but also change their style and content.



Open your code editor and create a new index.html file. Inside the HTML file, add the following code:

```html

<html>
  <body>
    <div></div>
  </body>
</html>
Then give the div a unique id so that you can target it later.

index.html

<html>
  <body>
    <div id="app"></div>
  </body>
</html>
To write JavaScript inside your HTML file, add a script tag:

index.html

<html>
  <body>
    <div id="app"></div>
    <script type="text/javascript"></script>
  </body>
</html>
Now, inside the script tag, you can use a DOM method, getElementById(), to select the <div> element by its id:

index.html

<html>
  <body>
    <div id="app"></div>
    <script type="text/javascript">
      const app = document.getElementById('app');
    </script>
  </body>
</html>
You can continue using DOM methods to create a new <h1> element:

index.html

<html>
  <body>
    <div id="app"></div>
    <script type="text/javascript">
      // Select the div element with 'app' id
      const app = document.getElementById('app');
 
      // Create a new H1 element
      const header = document.createElement('h1');
 
      // Create a new text node for the H1 element
      const text = 'Develop. Preview. Ship.';
      const headerContent = document.createTextNode(text);
 
      // Append the text to the H1 element
      header.appendChild(headerContent);
 
      // Place the H1 element inside the div
      app.appendChild(header);
    </script>
  </body>
</html>

To make sure everything is working, open your HTML file inside your browser of choice. You should see an h1 tag that says, 'Develop. Preview. Ship.'.

HTML vs. the DOM
If you look at the DOM elements inside your browser developer tools, you will notice the DOM includes the <h1> element. The DOM of the page is different from the source code - or in other words, the original HTML file you created.

Two side-by-side diagrams showing the differences between the rendered DOM elements and Source Code (HTML)
![alt text](image-1.png)
This is because the HTML represents the initial page content, whereas the DOM represents the updated page content which was changed by the JavaScript code you wrote.

Updating the DOM with plain JavaScript is very powerful but verbose. You've written all this code to add an <h1> element with some text:

    <script type="text/javascript">
  const app = document.getElementById('app');
  const header = document.createElement('h1');
  const text = 'Develop. Preview. Ship.';
  const headerContent = document.createTextNode(text);
  header.appendChild(headerContent);
  app.appendChild(header);
</script>
As the size of an app or team grows, it can become increasingly challenging to build applications this way.

With this approach, developers spend a lot of time writing instructions to tell the computer how it should do things. But wouldn't it be nice to describe what you want to show and let the computer figure out how to update the DOM?

# Imperative vs. declarative programming
The code above is a good example of imperative programming. You're writing the steps for how the user interface should be updated. But when it comes to building user interfaces, a declarative approach is often preferred because it can speed up the development process. Instead of having to write DOM methods, it would be helpful if developers were able to declare what they want to show (in this case, an h1 tag with some text).

In other words, imperative programming is like giving a chef step-by-step instructions on how to make a pizza. Declarative programming is like ordering a pizza without being concerned about the steps it takes to make the pizza. 🍕

React is a popular declarative library that you can use build user interfaces.
React: A declarative UI library
As a developer, you can tell React what you want to happen to the user interface, and React will figure out the steps of how to update the DOM on your behalf.

To use React in your newly created project, load two React scripts from an external website called unpkg.com:

react is the core React library.
react-dom provides DOM-specific methods that enable you to use React with the DOM.

```html
 <html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script type="text/javascript">
      const app = document.getElementById('app');
      const header = document.createElement('h1');
      const text = 'Develop. Preview. Ship.';
      const headerContent = document.createTextNode(text);
      header.appendChild(headerContent);
      app.appendChild(header);
    </script>
  </body>
</html>

Instead of directly manipulating the DOM with plain JavaScript, remove the DOM methods that you had added previously, and add the ReactDOM.createRoot() method to target a specific DOM element and create a root to display your React Components in. Then, add the root.render() method to render your React code to the DOM.

This will tell React to render our <h1> title inside our #app element.

<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script>
      const app = document.getElementById('app');
      const root = ReactDOM.createRoot(app);
      root.render(<h1>Develop. Preview. Ship.</h1>);
    </script>
  </body>
</html>
If you try to run this code in the browser, you will get a syntax error:

Terminal

Uncaught SyntaxError: expected expression, got '<'
This is because <h1>...</h1> is not valid Javascript. This piece of code is JSX.

# What is JSX?
JSX is a syntax extension for JavaScript that allows you to describe your UI in a familiar HTML-like syntax. The nice thing about JSX is that apart from following three JSX rules, you don't need to learn any new symbols or syntax outside of HTML and JavaScript.

But browsers don't understand JSX out of the box, so you'll need a JavaScript compiler, such as a Babel, to transform your JSX code into regular JavaScript.

Adding Babel to your project
To add Babel to your project, copy and paste the following script in your index.html file:

index.html

<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
In addition, you will need to inform Babel what code to transform by changing the script type to type=text/jsx.

index.html

<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <!-- Babel Script -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/jsx">
      const domNode = document.getElementById('app');
      const root = ReactDOM.createRoot(domNode);
      root.render(<h1>Develop. Preview. Ship.</h1>);
    </script>
  </body>
</html>
To confirm it's working correctly, open your HTML file in the browser.

Comparing the declarative React code you just wrote:

index.html

<script type="text/jsx">
  const domNode = document.getElementById("app")
  const root = ReactDOM.createRoot(domNode);
  root.render(<h1>Develop. Preview. Ship.</h1>);
</script>
to the imperative JavaScript code you wrote in the previous section:

index.html

<script type="text/javascript">
  const app = document.getElementById('app');
  const header = document.createElement('h1');
  const text = 'Develop. Preview. Ship.';
  const headerContent = document.createTextNode(text);
  header.appendChild(headerContent);
  app.appendChild(header);
</script>
You can start to see how using React enables you to cut down a lot of repetitive code.

And this is exactly what React does, it's a library that contains reusable snippets of code that perform tasks on your behalf - in this case, updating the UI.

Additional Resources:

You don't need to know exactly how React updates the UI to start using it, but if you'd like to learn more, here are some additional resources:

UI trees
Writing markup with JSX
react-dom/server sections in the React Documentation.
Essential JavaScript for React
While you can learn JavaScript and React at the same time, being familiar with JavaScript can make the process of learning React easier.

In the next sections, you will be introduced to some core concepts of React from a JavaScript perspective. Here's a summary of the JavaScript topics that will be mentioned:

Functions and Arrow Functions
Objects
Arrays and array methods
Destructuring
Template literals
Ternary Operators
ES Modules and Import / Export Syntax

# Chapter 3 Notes

Optimizing Fonts and Images
In the previous chapter, you learned how to style your Next.js application. Let's continue working on your home page by adding a custom font and a hero image.

In this chapter...

Here are the topics we’ll cover

How to add custom fonts with next/font.

How to add images with next/image.

How fonts and images are optimized in Next.js.

Why optimize fonts?
Fonts play a significant role in the design of a website, but using custom fonts in your project can affect performance if the font files need to be fetched and loaded.

Cumulative Layout Shift is a metric used by Google to evaluate the performance and user experience of a website. With fonts, layout shift happens when the browser initially renders text in a fallback or system font and then swaps it out for a custom font once it has loaded. This swap can cause the text size, spacing, or layout to change, shifting elements around it.

Mock UI showing initial load of a page, followed by a layout shift as the custom font loads.
Next.js automatically optimizes fonts in the application when you use the next/font module. It downloads font files at build time and hosts them with your other static assets. This means when a user visits your application, there are no additional network requests for fonts which would impact performance.

It’s time to take a quiz!
Test your knowledge and see what you’ve just learned.

How does Next.js optimize fonts?


A
It causes additional network requests which improve performance.

B
It disables all custom fonts.

C
It preloads all fonts at runtime.

D
It hosts font files with other static assets so that there are no additional network requests.

# Adding a primary font

Let's add a custom Google font to your application to see how this works.

In your /app/ui folder, create a new file called fonts.ts. You'll use this file to keep the fonts that will be used throughout your application.

Import the Inter font from the next/font/google module - this will be your primary font. Then, specify what subset you'd like to load. In this case, 'latin':

/app/ui/fonts.ts

import { Inter } from 'next/font/google';
 
export const inter = Inter({ subsets: ['latin'] });
Finally, add the font to the <body> element in /app/layout.tsx:

/app/layout.tsx

import '@/app/ui/global.css';
import { inter } from '@/app/ui/fonts';
 
export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body className={`${inter.className} antialiased`}>{children}</body>
    </html>
  );
}
By adding Inter to the <body> element, the font will be applied throughout your application. Here, you're also adding the Tailwind antialiased class which smooths out the font. It's not necessary to use this class, but it adds a nice touch.

Navigate to your browser, open dev tools and select the body element. You should see Inter and Inter_Fallback are now applied under styles.

Practice: Adding a secondary font
You can also add fonts to specific elements of your application.

Now it's your turn! In your fonts.ts file, import a secondary font called Lusitana and pass it to the <p> element in your /app/page.tsx file. In addition to specifying a subset like you did before, you should also specify different font weights. For example, 400 (normal) and 700 (bold).

Once you're ready, expand the code snippet below to see the solution.

Hints:

If you're unsure what weight options to pass to a font, check the TypeScript errors in your code editor.
Visit the Google Fonts website and search for Lusitana to see what options are available.
See the documentation for adding multiple fonts and the full list of options.
Finally, the <AcmeLogo /> component also uses Lusitana. It was commented out to prevent errors, you can now uncomment it:

/app/page.tsx

// ...
 
export default function Page() {
  return (
    <main className="flex min-h-screen flex-col p-6">
      <div className="flex h-20 shrink-0 items-end rounded-lg bg-blue-500 p-4 md:h-52">
        <AcmeLogo />
        {/* ... */}
      </div>
    </main>
  );
}
Great, you've added two custom fonts to your application! Next, let's add a hero image to the home page.

Why optimize images?
Next.js can serve static assets, like images, under the top-level /public folder. Files inside /public can be referenced in your application.

With regular HTML, you would add an image as follows:


<img
  src="/hero.png"
  alt="Screenshots of the dashboard project showing desktop version"
/>
However, this means you have to manually:

Ensure your image is responsive on different screen sizes.
Specify image sizes for different devices.
Prevent layout shift as the images load.
Lazy load images that are outside the user's viewport.
Image Optimization is a large topic in web development that could be considered a specialization in itself. Instead of manually implementing these optimizations, you can use the next/image component to automatically optimize your images.

The <Image> component
The <Image> Component is an extension of the HTML <img> tag, and comes with automatic image optimization, such as:

Preventing layout shift automatically when images are loading.
Resizing images to avoid shipping large images to devices with a smaller viewport.
Lazy loading images by default (images load as they enter the viewport).
Serving images in modern formats, like WebP and AVIF, when the browser supports it.
Adding the desktop hero image
Let's use the <Image> component. If you look inside the /public folder, you'll see there are two images: hero-desktop.png and hero-mobile.png. These two images are completely different, and they'll be shown depending if the user's device is a desktop or mobile.

In your /app/page.tsx file, import the component from next/image. Then, add the image under the comment:

/app/page.tsx

import AcmeLogo from '@/app/ui/acme-logo';
import { ArrowRightIcon } from '@heroicons/react/24/outline';
import Link from 'next/link';
import { lusitana } from '@/app/ui/fonts';
import Image from 'next/image';
 
export default function Page() {
  return (
    // ...
    <div className="flex items-center justify-center p-6 md:w-3/5 md:px-28 md:py-12">
      {/* Add Hero Images Here */}
      <Image
        src="/hero-desktop.png"
        width={1000}
        height={760}
        className="hidden md:block"
        alt="Screenshots of the dashboard project showing desktop version"
      />
    </div>
    //...
  );
}
Here, you're setting the width to 1000 and height to 760 pixels. It's good practice to set the width and height of your images to avoid layout shift, these should be an aspect ratio identical to the source image. These values are not the size the image is rendered, but instead the size of the actual image file used to understand the aspect ratio.

You'll also notice the class hidden to remove the image from the DOM on mobile screens, and md:block to show the image on desktop screens.

This is what your home page should look like now:

Styled home page with a custom font and hero image
Practice: Adding the mobile hero image
Now it's your turn! Under the image you've just added, add another <Image> component for hero-mobile.png.

The image should have a width of 560 and height of 620 pixels.
It should be shown on mobile screens, and hidden on desktop - you can use dev tools to check if the desktop and mobile images are swapped correctly.
Once you're ready, expand the code snippet below to see the solution.

# Recommended reading
There's a lot more to learn about these topics, including optimizing remote images and using local font files. If you'd like to dive deeper into fonts and images, see:

Image Optimization Docs : https://nextjs.org/docs/app/building-your-application/optimizing/images
Font Optimization Docs : https://nextjs.org/docs/app/building-your-application/optimizing/fonts
Improving Web Performance with Images (MDN) : https://developer.mozilla.org/en-US/docs/Learn/Performance/Multimedia
Web Fonts (MDN) : https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Web_fonts
How Core Web Vitals Affect SEO : https://vercel.com/blog/how-core-web-vitals-affect-seo
How Google handles JavaScript throughout the indexing process : https://vercel.com/blog/how-google-handles-javascript-throughout-the-indexing-process
