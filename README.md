# nginx
Config and setup instructions for nginx load balancer





** Build and configure nginx with pcre and openssl

  Download the souce to /usr/local/src or similar

    http://nginx.org
    http://pcre.org
    http://openssl.org

  Set this evironment variable:

    KERNEL_BITS=64

  From the nginx source directory,

    ./configure --with-pcre=/usr/local/src/pcre --with-openssl=/usr/local/src/openssl --with-http_ssl_module
    make
    sudo make install

  Test the build with

    nginx -V

** Configure ngix to proxy the proxibase server or servers

    cp nginx.conf.dev nginx.conf

  Nginx.conf is not tracked by git, so it will not be overridden.  Modify values as appropriate.

  In the nginx excutable drirectory, find the conf directory.

    rm nginx.conf
    ln -s /path/to/modified/ngix.conf

  Create the log files and set their permissions.

  Now test the config

    nginx -t

** Run it

  By default nginx runs in the background, so just

    nginx

  will start a master and worker process.

