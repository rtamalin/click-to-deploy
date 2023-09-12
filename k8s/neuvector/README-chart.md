# Click-to-Deploy chart sync-up with upstream chart

NOTE: The instructions below assume you have cloned my fork of the
click-to-deploy repo, namely github.com/rtamalin/click-to-deploy.git,
and not the upstream one.

The actual chart we are using, the neuvector/core chart, is being managed
in the github.com/SUSE-Enceladus/neuvector-chart-gks.git repo.

The version of the neuvector/core chart that we are working with exists on
the neuvector_chart branch in this repo, and the google_nv_deployer branch
is based upon that branch.

To update to a newer versio of the neuvector/core chart simply checkout the
neuvector_chart branch and copy the contents of the updated neuvector/core
chart over the k8s/neuvector/chart/neuvector, e.g. assuming both repos are
cloned beside each other, the you can used the following command to copy
the updated chart into this repo:

```shell
% rsync -a neuvector-helm-gks/charts/core/ k8s/neuvector/chart/neuvector/
```

Then commit the new changes and push them up to the neuvector_chart branch.

Next checkout google_nv_deployer branch, and rebase the branch contents on
top of the neuvector_chart branch, e.g.

```shell
% git checkout google_nv_deployer
% git rebase neuvector_chart
```

The number of conflicts, if any should be minimal; resolve them and then
force push the updated branch to the GitHub repo.
