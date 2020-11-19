# Charts Testing

### Lint Testing

Lint testing is performed on every pull request and is run by the Drone CI. The
configuration is stored in the [`test/ct.yaml`](/test/ct.yaml) file.

The Lint Testing currently:

* Performs [`ct lint`](https://github.com/guangbochen/chart-testing) on any changed charts to provide quick feedback


#### Run Lint Testing Locally

##### Using Docker Images:

```
docker run -d -it --name chart-test -v /path/to/your/charts/:/workdir/charts ranchercharts/chart-testing:v2.0.2-rancher3
docker exec -it chart-test sh 
cd workdir/charts/
git remote add dev-charts https://github.com/cnrancher/dev-charts
git fetch dev-charts master
ct lint --config test/ct.yaml
```

##### Using Binary Build:

You can download the [binary build](https://github.com/guangbochen/chart-testing/releases/tag/v2.0.2-rancher1) and run it locally using:

```
ct lint --config /path/to/your/charts/test/ct.yaml
```
