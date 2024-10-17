# Убираем www
<IfModule mod_rewrite.c>
	Options +FollowSymLinks
	RewriteEngine On
	RewriteBase / 
	RewriteCond %{HTTP_HOST} ^www.(.*)$
	RewriteCond %{REQUEST_URI} !local/*
	RewriteCond %{REQUEST_URI} !bitrix/*
	RewriteCond %{REQUEST_URI} !ajax/*
	RewriteCond %{REQUEST_URI} !upload/*
	RewriteCond %{REQUEST_URI} !include/* 
	RewriteCond %{QUERY_STRING} !http(s|)://
	RewriteCond %{QUERY_STRING} !(^|&).+($|&)
	RewriteRule ^(.*)$ https://%1/$1 [L,R=301]
</IfModule>
# Добавляем слеши в конце и убираем двойные
<IfModule mod_rewrite.c>
	Options +FollowSymLinks
	RewriteEngine On
	RewriteBase / 

	RewriteCond %{REQUEST_URI} (.*/[^/.]+)($|\?)
	RewriteCond %{REQUEST_URI} !\.html$
	RewriteCond %{REQUEST_URI} !(.*)/$
	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteCond %{REQUEST_URI} !local/*
	RewriteCond %{REQUEST_URI} !bitrix/*
	RewriteCond %{REQUEST_URI} !ajax/*
	RewriteCond %{REQUEST_URI} !upload/*  
	RewriteRule .* %1/ [R=301,L]

	RewriteCond %{REQUEST_URI} //
	RewriteCond %{REQUEST_URI} !local/*
	RewriteCond %{REQUEST_URI} !bitrix/*
	RewriteCond %{REQUEST_URI} !ajax/*
	RewriteCond %{REQUEST_URI} !upload/*
	RewriteCond %{REQUEST_URI} !include/* 
	RewriteCond %{QUERY_STRING} !http(s|)://
	RewriteCond %{QUERY_STRING} !(^|&).+($|&)
	RewriteRule .* https://%{HTTP_HOST}/$0 [R=301,L]
</IfModule>
