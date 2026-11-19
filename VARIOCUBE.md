# Variocube fork of nginx-proxy

This fork ships the nginx 1.31.9 security fix before upstream releases 1.11.7
(variocube/infrastructure#111).

Branch `variocube`: upstream main at bff2cdd (1.11.6-12-gbff2cdd) plus upstream PR #2792
(nginx 1.31.6 -> 1.31.9), cherry-picked. Upstream's Docker Hub publish workflows are removed;
only `.github/workflows/variocube-publish.yml` publishes.

## Publishing

    gh workflow run variocube-publish.yml -R variocube/nginx-proxy --ref variocube -f tag=1.11.6-12-gbff2cdd-nginx1.31.9

Builds, smoke-tests (nginx version, 503 on unknown host, `nginx -t`), pushes amd64+arm64 to
`ghcr.io/variocube/nginx-proxy:<tag>`. No `latest` tag.

## Exit plan

Once upstream releases nginx >= 1.31.9, switch back to `nginxproxy/nginx-proxy:<release>`
and archive this fork.
