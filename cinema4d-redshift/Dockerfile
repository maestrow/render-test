FROM nvidia/cudagl:9.0-runtime-centos7

RUN echo -e "192.168.1.104\thost.docker.internal\n" >> /etc/hosts && \
\
    curl http://host.docker.internal:8080/Cinema4D-21.209_centos7_clr-RB305619.x86_64.rpm -o cinema4d.rpm && \
    yum install -y webkitgtk4-2.22.7-2.el7.x86_64 cinema4d.rpm && \
    rm cinema4d.rpm && \
    yum clean all && \
    rm -rf /var/cache/yum && \
\
    curl http://host.docker.internal:8080/redshift_v2.6.53_linux_demo.run -o redshift.run && \
    chmod +x redshift.run && \
    echo accept | ./redshift.run && \
    rm redshift.run && \
\
    cp -r /usr/redshift/redshift4c4d/R21/Redshift $(ls -d /opt/maxon/*/bin/plugins) && \
\
    ln -s /usr/redshift/bin/redshiftCmdLine /usr/local/bin/ && \
    yum install -y http://repo.okay.com.mx/centos/7/x86_64/release/okay-release-1-1.noarch.rpm && \
    yum install -y libopencl-devel && \
\
    mkdir /render

COPY c4d login /
COPY balltest.c4d /render
ENTRYPOINT ["/c4d"]
