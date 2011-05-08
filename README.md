# HumMod Documentation

This is the documentation for HumMod projects.

## How to contribute?
1. Fork the repository.
2. Clone your repository: `> git clone git@github.com:your-username/documentation.git`
3. Switch to the `gh-pages` branch: `> git checkout gh-pages`
4. Get to work.
5. Push changes into branch: `> git push origin gh-pages`
6. Submit Pull Request.  Please include a good description of what your changes entail.

## About Styles
We try to keep the look of the HumMod sites uniform.  As such, please do not override styles.  If you encounter a problem, [contact us](http://hummod.org/contact) and we'll see what can be done.

All pages should use the `default.html` layout.  As we finalize the styles and appropriate tags, the README will be updated.

## Structure
Each page is divided into sections.  These sections should have header tags with an h1 element inside.

Place the pertinent content outside the header but inside the section.

Here's an example:
```
<section id="example-section">
  <header>
    <h1>This is an example of a section</h1>
    <a href="#block">Back to the top.</a>
  </header>
  <p>
    Sections should be structured like this example.  Please note the section, header, and h1 tags.  Further, the section has an id that corresponds to the sections header.  This unique id is used for linking within the page.
  </p>
  <p>
    Since we link inside the page, it's necessary to update the main nav group up top.
  </p>
</section>
``` 

### Tags and Usage
In progress.