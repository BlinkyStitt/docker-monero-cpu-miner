# Monero CPU Miner

Docker-compose file for running the xmr-stak-cpu miner. It is probably faster to run native code, but this makes it easy

If you want to use this yourself, create a `cpu_miner.env` file next to this `docker-compose.yml` . See the [miner's entrypoint script](https://github.com/WyseNynja/xmr-stak-cpu/blob/master/docker-entrypoint.sh) for available settings. It should look something like this:

    LOGIN=4YOURMONEROADDRESSHERE...+1800
    MAX_CPUS=1
    PASS=yourcomputername
    POOL=mine.xmrpool.net:443
    USE_SLOW_MEMORY=warn
    USE_TLS=true

Experiment with different share difficulties (or don't set any). 1800 works well for my 2011 MacBook Air. You want a share at least every 60 seconds on most pools.

Usage on Mac/Linux:

    git clone https://github.com/WyseNynja/docker-monero-cpu-miner.git

    cd docker-monero-cpu-miner

    # set variables for your pool
    $EDITOR .env

    docker-compose pull
    docker-compose up -d
    open http://localhost:8000

This should also work on Windows, but I haven't tried it there. It probably won't be as fast as a native miner.
