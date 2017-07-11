nginx-rpm
=========

Nginx For CentOS 7

Nginx 1.10.2 patched with the following modules:

``` bash

--with-http_ssl_module \
--with-http_realip_module \
--with-http_addition_module \
--with-http_sub_module \
--with-http_dav_module \
--with-http_flv_module \
--with-http_mp4_module \
--with-http_gunzip_module \
--with-http_gzip_static_module \
--with-http_random_index_module \
--with-http_secure_link_module \
--with-http_stub_status_module \
--with-http_auth_request_module \
--with-http_image_filter_module \
--with-mail \
--with-mail_ssl_module \
--with-file-aio \
--with-debug \
--with-ipv6 \
--with-http_v2_module

# Exteranl modules

lua-nginx-module-0.10.6
echo-nginx-module-0.56
ngx_http_trim_filter_module
headers-more-nginx-module-0.25
ngx_cache_purge-2.3
ngx_txid
ngx_pagespeed-latest-stable
```

``` bash
git clone https://github.com/doubaokun/nginx-rpm
cd ~/nginx-rpm
mv .rpmmacros ../.rpmmacros
yum -y install rpm-build
yum -y install openssl-devel zlib-devel pcre-devel gcc lua-devel gd-devel

# or
#yum-builddep ~/nginx-rpm/rpmbuild/SPECS/nginx.spec

yum install centos-release-scl
yum install devtoolset-4-gcc*
scl enable devtoolset-4 bash

cd ~/nginx-rpm/rpmbuild/SOURCES/
tar zxvf ngx_pagespeed-1.11.33.4.tar.gz
cd ngx_pagespeed-latest-stable/
wget https://dl.google.com/dl/page-speed/psol/1.11.33.4.tar.gz
tar zxvf 1.11.33.4.tar.gz
rm -rf 1.11.33.4.tar.gz
cd ../
tar zcvf ngx_pagespeed-1.11.33.4.tar.gz ngx_pagespeed-latest-stable
rm -rf ngx_pagespeed-latest-stable

rpmbuild -ba ~/nginx-rpm/rpmbuild/SPECS/nginx.spec

cd ~/nginx-rpm/rpmbuild/RPMS/x86_64
yum -y install ./nginx-1.10.2-4.el7.centos.ngx.x86_64.rpm
```