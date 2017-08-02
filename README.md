# Monero CPU Miner behind Tor

Docker-compose file for running the xmr-stak-cpu miner (partly) behind Tor.

If you want to use this yourself, modify the POOL and LOGIN in the docker-compose file. See the [miner's entrypoint script](https://github.com/WyseNynja/xmr-stak-cpu/blob/master/docker-entrypoint.sh) for available settings.

**WARNING!** The miner isn't able to resolve DNS queries over Tor. I'm not actually sure how much is leaking. The external network should be removed from the cpu_miner container before this is actually used with the expectation of private mining.

Usage:

    git clone https://github.com/WyseNynja/docker-monero-cpu-miner.git

    cd docker-monero-cpu-miner

    # edit docker-compose.yaml to include your settings
    # TODO: use .env files?
    $EDITOR docker-compose.yaml

    docker-compose pull && docker-compose up -d && open http://localhost:8000

Monitor Tor traffic:

    docker-compose exec tor arm

NOTE: for even more anonymity, run docker-compose with torsocks, too
