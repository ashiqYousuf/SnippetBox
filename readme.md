# Snippetbox

## Note:- This readme file contains the important concepts that I learnt while building this application.

### Servemux:
1. Router is equivalent to *servemux* in go. Usually we have one *servemux* for our app containing all our routes.

2. Request goes to the => Go Server (passes it to)  => *servemux's ServeHTTP() method*=> in-turn calls *handler's ServeHTTP() method*

3. *servemux* treats "/" as catch-all.

4. Goʼs *servemux* supports two different types of URL patterns: fixed paths (/api/users) *exact match* and subtree paths (/api/users/) *wildcard match*. Fixed paths donʼt end with a trailing slash, whereas subtree paths do end with a trailing slash.

5. So, for the sake of security, itʼs generally a good idea to avoid *DefaultServeMux*.

6. In Goʼs *servemux*, longer URL patterns always take precedence over shorter ones. Request URL paths are automatically sanitized. host-specific maths are precedenced than non-host specific patterns.

7. All incoming HTTP requests are served in their own goroutine. Go Server is Concurrent!

### Project Structure
1. The cmd directory will contain the application-specific code for the executable applications in the project. It scales nicely to add another app later on (cmd/cli).
2. The ui directory will contain the user-interface assets used by the web app.
3. Packages which live in internal directory (helpers|db models) can only be imported by code inside our snippetbox project.

### Templating
1. {{template}} action is used to invoke one template from another. But Go also provides a {{block}}...{{end}} action which you can use instead.

### File Server
1. Go has built-in *http.FileServer* handler which you can use to serve files over HTTP from a specific dir.
2. It sanitizes all request paths by running them through the *path.Clean()* function before searching for a file.
3. Range requests are fully supported. This is great if your application is serving large files and you want to support resumable downloads.
4. The Last-Modified and If-Modified-Since headers are supported.

### Dependency Injection
1. Most web apps will have multiple dependencies that their handlers need to access (db conn, centralized err handlers...). How can we make any dependency available to our handlers? (i) use global vars (❌) (ii) inject dependencies (✅).
For apps where all handlers are in the same package, a neat way to inject deps is to put them into a custom *application* struct, and then define your handler functions as methods against *application*.

