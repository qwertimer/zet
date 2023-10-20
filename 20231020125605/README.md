# Using Distrobox to bring packages into your distro.

Distrobox has an absolutely amazing feature where you can download the
package inside the distrobox and export it into your own main os. We can
use the below command to do this

```
distrobox-export --bin /bin/<package> --export-path
<location_to_install_to> 
```

Allowing us to get bleeding edge programs into ubuntu or debian.

