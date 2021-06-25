# GoWiki
Go implementation of a simple Wiki.

This code is based on one of the official Golang Tutorials here: https://golang.org/doc/articles/wiki/

Added features:

- Index page at "/" path to show list of available pages.
- Create a new page from the Index page.
- Delete function. It is possible to delete pages from the index page and the view page.

Running the application will launch a webserver listening on the port 8080. 

Open the `http://localhost:8080/` in a browser or any HTTP client to access the Index page of our GoWiki site. Here there is a list of available pages that can be viewed and it is possible to create a new page. Navigation between the Index page and View/Edit are possible via links placed on the sites. Full CRUD functionalites have been implemented.

Directly visiting the `http://localhost:8080/view/<page title>` URL it is possible to view the content of the `<page title>.txt` text file under the `/pages` folder. If the title does not exist a `Page Not Found` page will be presented with a button to create a page with the given title. Similar to the View directly visiting the `http://localhost:8080/edit/<page title>` URL it is possible to edit the content of the title if exists, otherwise new page can be created.


## Covered in this tutorial

- Creating a data structure with load and save methods
- Using the net/http package to build web applications
- Using the html/template package to process HTML templates
- Using the regexp package to validate user input
- Using closures


### Wiki page data structure

```
type Page struct {
    Title string
    Body  []byte
}
```

### Application functions

1. Listing pages

At the root path '/' the Index page shows the available Wiki pages (lists the .txt files under the pages folder).

2. Creating pages

By visiting the `/view/<page title>` or `/edit/<page title>` URL with a page title that does not exist a new page can be created. In addition to that it is possible to provide a title on the Index page and clicking on the 'Create new page' button.

At the root path '/' the Index page shows the available Wiki pages (lists the `.txt` files under the `/pages` folder).

3. Viewing pages

To show the content of a page visit `/view/<page title>` URL. However, on the Index page the titles are links that brings the user to this view. 

4. Editing pages

To edit a Title visit the `/edit/<page title>` URL or use the 'edit' link on a page viewed.

5. Delete pages

Delete links are available on the Index page next to the titles and on the view page. This removes the given `.txt` file under the `/pages` folder

### Building and running the application

```
$ go build wiki.go
$ ./wiki
```