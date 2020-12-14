- Django is a free and open source, high-level Python Web framework that encourages rapid development and clean, pragmatic design. 

### Install
- If you’d like to be able to update your Django code occasionally with the latest bug fixes and improvements, follow these instructions:
  - Make sure that you have Git installed and that you can run its commands from a shell. (Enter git help at a shell prompt to test this.)
  - Check out Django’s main development branch like so:
    - `git clone https://github.com/django/django.git`
    - This will create a directory django in your current directory.
  - Make sure that the Python interpreter can load Django’s code. The most convenient way to do this is to use a virtual environment and pip. The contributing tutorial walks through how to create a virtual environment.
  - After setting up and activating the virtual environment, run the following command:
    - `python -m pip install -e django/`
  - This will make Django’s code importable, and will also make the django-admin utility command available. In other words, you’re all set!
- When you want to update your copy of the Django source code, run the command git pull from within the django directory. When you do this, Git will download any changes.
- If you decide to use the latest development version of Django, you’ll want to pay close attention to the development timeline, and you’ll want to keep an eye on the release notes for the upcoming release. This will help you stay on top of any new features you might want to use, as well as any changes you’ll need to make to your code when updating your copy of Django. (For stable releases, any necessary changes are documented in the release notes.)
- To verify that Django can be seen by Python, type python from your shell. Then at the Python prompt, try to import Django:
`>>> import django`
`>>> print(django.get_version())`

# [Getting started with Django](https://www.djangoproject.com/start/)
### Object-relational mapper
- Deﬁne your data models entirely in Python. You get a rich, dynamic database-access API for free — but you can still write SQL if needed.
- Django uses the attributes of classes/objects to assign data to a database column. 
- the table's name is automatically derived from the metadata but can be overridden.
- an ID field is added automatically but can be overridden

### URLs and views
- To design URLs for an application, you create a Python module called a URLconf. Like a table of contents for your app, it contains a simple mapping between URL patterns and your views.

### Templates
- A variable outputs a value from the context, which is a dict-like object mapping keys to values.
  - Variables are surrounded by {{ and }} 
- Dictionary lookup, attribute lookup and list-index lookups are implemented with a dot notation
  - `{{ my_dict.key }}`
  - `{{ my_object.attribute }}`
  - `{{ my_list.0 }}`
- Tags provide arbitrary logic in the rendering process.
  - This definition is deliberately vague. For example, a tag can output content, serve as a control structure e.g. an “if” statement or a “for” loop, grab content from a database, or even enable access to other template tags.
  - Tags are surrounded by {% and %}
  - Most tags accept args
  - Some tags require beginning and ending tags 
- Filters transform the values of variables and tag arguments.
  - `{{ my_date|date:"Y-m-d" }}`
  - renders the date in a year-month-day format

### Forms
- Django provides a range of tools and libraries to help you build forms to accept input from site visitors, and then process and respond to the input.
- As well as its <input> elements, a form must specify two things:
  - where: the URL to which the data corresponding to the user’s input should be returned
  - how: the HTTP method the data should be returned by
- GET and POST are the only HTTP methods to use when dealing with forms
  - Django’s login form is returned using the POST method, in which the browser bundles up the form data, encodes it for transmission, sends it to the server, and then receives back its response.
  - GET, by contrast, bundles the submitted data into a string, and uses this to compose a URL. The URL contains the address where the data must be sent, as well as the data keys and values. 
- Django handles three distinct parts of the work involved in forms:
  - preparing and restructuring data to make it ready for rendering
  - creating HTML forms for the data
  - receiving and processing submitted forms and data from the client
- At the heart of this system of components is Django’s Form class. In much the same way that a Django model describes the logical structure of an object, its behavior, and the way its parts are represented to us, a Form class describes a form and determines how it works and appears.
  - In a similar way that a model class’s fields map to database fields, a form class’s fields map to HTML form <input> elements. (A ModelForm maps a model class’s fields to HTML form <input> elements via a Form; this is what the Django admin is based upon.)
  - A form’s fields are themselves classes; they manage form data and perform validation when a form is submitted. A DateField and a FileField handle very different kinds of data and have to do different things with it.
  - A form field is represented to a user in the browser as an HTML “widget” - a piece of user interface machinery. Each field type has an appropriate default Widget class, but these can be overridden as required.

### Authentication
- Django comes with a full-featured and secure authentication system. It handles user accounts, groups, permissions and cookie-based user sessions. This lets you easily build sites that allow users to create accounts and safely log in/out.
- The Django authentication system handles both authentication and authorization. Briefly, authentication verifies a user is who they claim to be, and authorization determines what an authenticated user is allowed to do. Here the term authentication is used to refer to both tasks.
- The auth system consists of:
  - Users
  - Permissions: Binary (yes/no) flags designating whether a user may perform a certain task.
  - Groups: A generic way of applying labels and permissions to more than one user.
  - A configurable password hashing system
  - Forms and view tools for logging in users, or restricting content
  - A pluggable backend system
The authentication system in Django aims to be very generic and **doesn’t** provide some features commonly found in web authentication systems. Solutions for some of these common problems have been implemented in third-party packages:
  - Password strength checking
  - Throttling of login attempts
  - Authentication against third-parties (OAuth, for example)
  - Object-level permissions

### Admin
- One of the most powerful parts of Django is the automatic admin interface. It reads metadata from your models to provide a quick, model-centric interface where trusted users can manage content on your site. The admin’s recommended use is limited to an organization’s internal management tool. It’s not intended for building your entire front end around.
- The admin has many hooks for customization, but beware of trying to use those hooks exclusively. If you need to provide a more process-centric interface that abstracts away the implementation details of database tables and fields, then it’s probably time to write your own views.
- The admin is enabled in the default project template used by startproject.

### Internationalization
- The goal of internationalization and localization is to allow a single Web application to offer its content in languages and formats tailored to the audience.
- Django has full support for translation of text, formatting of dates, times and numbers, and time zones.
- Essentially, Django does two things:
  - It allows developers and template authors to specify which parts of their apps should be translated or formatted for local languages and cultures.
  - It uses these hooks to localize Web apps for particular users according to their preferences.
  - Translation depends on the target language, and formatting usually depends on the target country. This information is provided by browsers in the Accept-Language header. However, the time zone isn’t readily available.

### Security
- Django provides multiple protections against:
  - Clickjacking
    - Clickjacking is a type of attack where a malicious site wraps another site in a frame. This attack can result in an unsuspecting user being tricked into performing unintended actions on the target site.
    - Django contains clickjacking protection in the form of the X-Frame-Options middleware which in a supporting browser can prevent a site from being rendered inside a frame. It is possible to disable the protection on a per view basis or to configure the exact header value sent.
  - Cross-site scripting
    - XSS attacks allow a user to inject client side scripts into the browsers of other users. This is usually achieved by storing the malicious scripts in the database where it will be retrieved and displayed to other users, or by getting users to click a link which will cause the attacker’s JavaScript to be executed by the user’s browser. However, XSS attacks can originate from any untrusted source of data, such as cookies or Web services, whenever the data is not sufficiently sanitized before including in a page.
    - Using Django templates protects you against the majority of XSS attacks. Django templates escape specific characters which are particularly dangerous to HTML. While this protects users from most malicious input, it is not entirely foolproof. 
    - It is also important to be particularly careful when using is_safe with custom template tags, the safe template tag, mark_safe, and when autoescape is turned off.
    - You should also be very careful when storing HTML in the database, especially when that HTML is retrieved and displayed.
  - Cross Site Request Forgery (CSRF)
    - CSRF attacks allow a malicious user to execute actions using the credentials of another user without that user’s knowledge or consent.
    - CSRF protection works by checking for a secret in each POST request. This ensures that a malicious user cannot “replay” a form POST to your website and have another logged in user unwittingly submit that form. The malicious user would have to know the secret, which is user specific (using a cookie).
    - When deployed with HTTPS, CsrfViewMiddleware will check that the HTTP referer header is set to a URL on the same origin (including subdomain and port). Because HTTPS provides additional security, it is imperative to ensure connections use HTTPS where it is available by forwarding insecure connection requests and using HSTS for supported browsers.
    - Be very careful with marking views with the csrf_exempt decorator unless it is absolutely necessary.
  - SQL injection
    - SQL injection is a type of attack where a malicious user is able to execute arbitrary SQL code on a database. This can result in records being deleted or data leakage.
    - Django’s querysets are protected from SQL injection since their queries are constructed using query parameterization. A query’s SQL code is defined separately from the query’s parameters. Since parameters may be user-provided and therefore unsafe, they are escaped by the underlying database driver.
  - Remote code execution



# [How Django Works Behind the Scenes](https://wsvincent.com/how-django-works-behind-the-scenes/)
- Django’s code is open source and available to all. 
- Django’s organization is managed by a non-profit (since 2008), the Django Software Foundaton, with a miniscule budget.
  - The DSF handles legal, financial, and administrative matters for Django
  - The largest expense, by far, is the Fellows Program, paid contractors who triage tickets, manage releases, and generally perform the unsexy but necessary work needed to keep Django on track.
- Django code is lead by a core team of volunteers, two paid Django Fellows, and a larger group of contributors.
  - Tim Graham was the inaugural fellow during its 3-month pilot in the fall of 2014 and became a full-time fellow in 2015. He remained in this role until 2018 before transitioning to a part-time role. Carlton Gibson joined as a part-time Fellow in 2018 and in 2019 Mariusz Felisiak took over from Tim Graham.
  - The majority of donations goes to the Django Fellows who ensure the project remains on track and the rest helps promote Django and expand its community. The total budget for the DSF in 2019 is around $200,000, or less than the cost of a single Bay Area Django engineer.
  - Adrian Holovaty and Jacob Kaplan-Moss functioned as Django’s dual-BDFLs (Benevolent Dictator for Life) from 2005 until their retirement in 2014.
  - Django has a small, core team of trusted volunteers who work alongside the Django Fellows to manage technical side of the Django Project. Django Core members are divided into teams that have authority over the Django Project infrastructure
