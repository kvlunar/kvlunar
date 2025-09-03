# 🪐 Backend Engineer Challenge: Rockets 🚀

Solution contains two services: [event-facade](https://github.com/kvlunar/rockets-event-facade) and [dashboard](https://github.com/kvlunar/rockets-dashboard). It requires [Node.js 22](https://nodejs.org/en/download).

## Deployment

Clone [the glue repo](https://github.com/kvlunar/rockets-glue) into a directory called `glue` next where you cloned the services

```sh
$ git clone https://github.com/kvlunar/rockets-glue.git glue
```

To deploy and run it, you need valid AWS credentials. If you don't feel comfortable with that, you can use pre-deployed services here:

- event-facade: https://5bvo1s8en7.execute-api.eu-central-1.amazonaws.com/
- dashboard: https://auxixcjav3.execute-api.eu-central-1.amazonaws.com/

## Usage

Launch rockets using

```sh
$ rockets launch https://5bvo1s8en7.execute-api.eu-central-1.amazonaws.com/messages
```

Dashboard JSON endpoint is available at the root of the service. Here's a nifty one-liner for monitoring rockets in the terminal:

```sh
$ watch -c -d -n 1 "curl -s https://auxixcjav3.execute-api.eu-central-1.amazonaws.com/ | jq -r '(.[0] | keys_unsorted) as \$keys | \$keys, map([.[ \$keys[] ]])[] | @tsv' | column -t"
```

Clear rocket status data and dashboard using

```sh
$ curl -X POST https://auxixcjav3.execute-api.eu-central-1.amazonaws.com/reset
```
