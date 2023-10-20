# NO_PUBKEY-gpg-error-Fix
Fixes the gpg error NO_PUBKEY with a one-liner

<code>`sudo apt update 2>&1 1>/dev/null | sed -ne 's/.*NO_PUBKEY //p' | while read key; do if ! [[ ${keys[*]} =~ "$key" ]]; then sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys "$key"; keys+=("$key"); fi; done`</code>
