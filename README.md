nginx-rpm
=========


Updated to 1.10.2

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
    sudo yum -y install openssl-devel zlib-devel pcre-devel gcc lua-devel gd-devel liboboe-devel
    #Or
    yum-builddep ~/nginx-rpm/rpmbuild/SPECS/nginx.spec


    rpm --import https://linux.web.cern.ch/linux/scientific6/docs/repository/cern/slc6X/i386/RPM-GPG-KEY-cern
    wget -O /etc/yum.repos.d/slc6-devtoolset.repo https://linux.web.cern.ch/linux/scientific6/docs/repository/cern/devtoolset/slc6-devtoolset.repo
    yum install devtoolset-2-gcc-c++ devtoolset-2-binutils

    cd ~/nginx-rpm/rpmbuildSOURCES/
    tar zxvf ngx_pagespeed-1.11.33.4.tar.gz
    cd ngx_pagespeed-latest-stable/
    wget https://dl.google.com/dl/page-speed/psol/1.11.33.4.tar.gz
    tar zxvf 1.11.33.4.tar.gz
    rm -rf 1.11.33.4.tar.gz
    cd ../
    tar zcvf ngx_pagespeed-1.11.33.4.tar.gz ngx_pagespeed-latest-stable
    rm -rf ngx_pagespeed-latest-stable

    rpmbuild -ba ~/nginx-rpm/rpmbuild/SPECS/nginx.spec

    cd /home/bruce/nginx-rpm/rpmbuild/RPMS/x86_64
    yum install nginx-1.6.2-1.el6.ngx.x86_64.rpm
