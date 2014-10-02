nginx-rpm
=========

Nginx 1.6.2 patched with the following modules:

    --with-http_image_filter_module \
    --add-module=%{_builddir}/%{name}-%{version}/lua-nginx-module-0.9.12 \
    --add-module=%{_builddir}/%{name}-%{version}/echo-nginx-module-0.56 \
    --add-module=%{_builddir}/%{name}-%{version}/ngx_http_trim_filter_module \
    --add-module=%{_builddir}/%{name}-%{version}/headers-more-nginx-module-0.25 \
