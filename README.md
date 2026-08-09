# once-google

Desired state for an [ONCE](https://github.com/getcolors/once) server on Google
Cloud. The deployment uses Cloudflare for DNS, Resend for SMTP, and a local
OpenTofu backend.

```sh
./green build
./green create --dry-run
./green create
./green delete
```

`colors.yml` is the only file normally edited. Keep credentials in the ignored
`.envrc.private` as `COLORS_PAR_*` variables; Google Cloud authentication uses
the native gcloud credential chain.

The committed `compute-prevent-destroy: true` guards deletion. Lift it only for
one intentional run with `COLORS_PAR_COMPUTE_PREVENT_DESTROY=false`.

The local backend means state under `.colors/` is not committed or shared. Do
not remove that directory while the deployment exists.
