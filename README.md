# Manually Forcing HTTPS Instructions for a Website on HostGator

1. Access your CPanel found here https://gator4202.hostgator.com:2083/
2. Click "file manager"
3. Click "Setting" (top right corner)
4. Click "Show Hidden Files (Dotfiles)"
5. Right Click .htaccess file and Click "Code Edit"
6. Replace the "OLD CODE" WITH THE "REWRITTEN CODE" BELOW
7. Click "Save Changes"
## OLD CODE BELOW (Default with hostgator)

RewriteEngine on
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME}\.html -f
RewriteCond %{REQUEST_URI} !^/\.well-known/acme-challenge/[0-9a-zA-Z_-]+$
RewriteCond %{REQUEST_URI} !^/\.well-known/cpanel-dcv/[0-9a-zA-Z_-]+$
RewriteCond %{REQUEST_URI} !^/\.well-known/pki-validation/[A-F0-9]{32}\.txt(?:\ Comodo\ DCV)?$
RewriteRule ^(.*)$ $1.html


## REWRITTEN CODE BELOW

RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

Reference:https://www.hostgator.com/help/article/hostgator-free-ssl?utm_campaign=email-clm&utm_medium=email&utm_source=email-HGfreessl-email2
