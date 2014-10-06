nginx-rpm
=========

Nginx 1.6.2 patched with the following modules:

    --with-http_image_filter_module \
    --add-module=%{_builddir}/%{name}-%{version}/lua-nginx-module-0.9.12 \
    --add-module=%{_builddir}/%{name}-%{version}/echo-nginx-module-0.56 \
    --add-module=%{_builddir}/%{name}-%{version}/ngx_http_trim_filter_module \
    --add-module=%{_builddir}/%{name}-%{version}/headers-more-nginx-module-0.25 \



cd ~/nginx-rpm
git clone https://github.com/doubaokun/nginx-rpm
mv .rpmmacros ../.rpmmacros
sudo yum -y install rpm-build
sudo yum -y install openssl-devel zlib-devel pcre-devel gcc lua-devel gd-devel
rpmbuild -ba ~/nginx-rpm/rpmbuild/SPECS/nginx.spec

cd /home/bruce/nginx-rpm/rpmbuild/RPMS/x86_64
yum install nginx-1.6.2-1.el6.ngx.x86_64.rpm
