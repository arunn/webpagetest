# webpagetest
Docker modified to work in Ubuntu 16.04 for traffic shaping


# how to use

1) Clone the repository to local(git clone git@github.com:arunn/webpagetest)
2) cd webpagetest/localserver/
3) docker build -t local-wptserver .
4) cd ../localagent/
5) docker build -t local-wptagent .
6) docker run -d -p 4000:80 local-wptserver
7) docker run -d -p 4001:80 \
    --network="host" \
    -e "SERVER_URL=http://localhost:4000/work/" \
    -e "LOCATION=Test" \
    local-wptagent
    
8) access http://localhost:4000 to start testing
