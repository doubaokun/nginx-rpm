nginx-rpm
=========

For CentOS 7

Nginx updated to 1.10.2

Nginx 1.10.2 patched with the following modules:

``` bash
--with-http_image_filter_module \
--add-module=%{_builddir}/%{name}-%{version}/lua-nginx-module-0.9.12 \
--add-module=%{_builddir}/%{name}-%{version}/echo-nginx-module-0.56 \
--add-module=%{_builddir}/%{name}-%{version}/ngx_http_trim_filter_module \
--add-module=%{_builddir}/%{name}-%{version}/headers-more-nginx-module-0.25 \
```

``` bash
git clone https://github.com/doubaokun/nginx-rpm
cd ~/nginx-rpm
mv .rpmmacros ../.rpmmacros
yum -y install rpm-build
yum -y install openssl-devel zlib-devel pcre-devel gcc lua-devel gd-devel
#Or
yum-builddep ~/nginx-rpm/rpmbuild/SPECS/nginx.spec

rpm --import https://linux.web.cern.ch/linux/scientific6/docs/repository/cern/slc6X/i386/RPM-GPG-KEY-cern
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
yum install nginx-1.6.2-1.el6.ngx.x86_64.rpm
```