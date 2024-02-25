# Snippetbox

## Note:- This readme file contains the important concepts that I learnt while building this application.

1. Router is equivalent to *servemux* in go. Usually we have one *servemux* for our app containing all our routes.

2. Request => Go Server (pass)=> servemux (dispatches)=> handler

3. *servemux* treats "/" as catch-all.

4. Goʼs *servemux* supports two different types of URL patterns: fixed paths (/api/users) *exact match* and subtree paths (/api/users/) *wildcard match*. Fixed paths donʼt end with a trailing slash, whereas subtree paths do end with a trailing slash.

5. So, for the sake of security, itʼs generally a good idea to avoid *DefaultServeMux*.

6. In Goʼs *servemux*, longer URL patterns always take precedence over shorter ones. Request URL paths are automatically sanitized. host-specific maths are precedenced than non-host specific patterns

