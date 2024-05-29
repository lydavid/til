
# Setting up Custom Subdomain for GitHub Pages
Follow the steps from https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site?platform=linux#configuring-a-subdomain, log into a DNS provider such as WHC, click "Manage", click the gear icon, click "Advanced DNS Manager", go to DNS Records, and add a record:
- Name: `til.da`
- TTL: `3600` (Middle-ground. WHC defaults to 14440. Cloudflare defaults to 300[^1]. Cloudflare doesn't charge for DNS queries on the Free plan[^2])
- Type: `CNAME`
- Value: `lydavid.github.io`

Verify using dig. Make sure the GitHub Pages servers appears.
```
dig til.da.vidly.ca +nostats +nocomments +nocmd
```

```
;til.da.vidly.ca.               IN      A
til.da.vidly.ca.        0       IN      CNAME   lydavid.github.io.
lydavid.github.io.      0       IN      A       185.199.111.153
lydavid.github.io.      0       IN      A       185.199.108.153
lydavid.github.io.      0       IN      A       185.199.109.153
lydavid.github.io.      0       IN      A       185.199.110.153
```

Go to https://github.com/lydavid/til/settings/pages, and set the custom domain as `til.da.vidly.ca`.

See an error saying:
> til.da.vidly.ca is improperly configured
> Domain does not resolve to the GitHub Pages server. For more information, see [documentation](https://docs.github.com/articles/setting-up-a-custom-domain-with-github-pages/) (NotServedByPagesError).

But this is expected. Just wait for DNS propagation[^3].

I waited before pushing this, and it did work.

[^1]: https://developers.cloudflare.com/dns/manage-dns-records/reference/ttl/
[^2]: https://developers.cloudflare.com/dns/troubleshooting/faq/#does-cloudflare-charge-for-or-limit-dns-queries
[^3]: https://stackoverflow.com/a/54078569