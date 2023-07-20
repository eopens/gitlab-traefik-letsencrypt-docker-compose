# GitLab with Let's Encrypt in a Docker Compose

Install Docker Engine and Docker Compose by following my [guide](https://www.heyvaldemar.com/install-docker-engine-and-docker-compose-on-ubuntu-server/).

Deploy GitLab server with a Docker Compose using the command:

`docker compose -f gitlab-traefik-letsencrypt-docker-compose.yml -p gitlab up -d`

Visit the GitLab URL, and sign in with the username `root` and the password from the following command:

`sudo docker exec -it $(sudo docker ps -aqf "name=gitlab-gitlab-1") grep 'Password:' /etc/gitlab/initial_root_password`

Get the GitLab Runner's registration token via this link (replace domain with yours):

`https://gitlab.heyvaldemar.net/admin/runners`

Register the GitLab Runner with an obtained token:

```
REGISTRATION_TOKEN=125DGwcgyrAsVVjUkxTL \
&& docker exec -it $(sudo docker ps -aqf "name=gitlab-runner-1") gitlab-runner register \
--non-interactive \
--url "http://gitlab/" \
--registration-token "$REGISTRATION_TOKEN" \
--executor "docker" \
--docker-image docker:stable \
--description "docker-runner-1" \
--tag-list "docker,linux" \
--run-untagged="true" \
--docker-privileged \
--output-limit "50000000" \
--access-level="not_protected" \
--docker-volumes "/var/run/docker.sock:/var/run/docker.sock"
```

# Author
hey, I’m Vladimir Mikhalev, but my friends call me Valdemar.

🌐 My [website](https://www.heyvaldemar.com/) with detailed IT guides\
🎬 Follow me on [YouTube](https://www.youtube.com/channel/UCf85kQ0u1sYTTTyKVpxrlyQ?sub_confirmation=1)\
🐦 Follow me on [Twitter](https://twitter.com/heyValdemar)\
🎨 Follow me on [Instagram](https://www.instagram.com/heyvaldemar/)\
🎸 Follow me on [Facebook](https://www.facebook.com/heyValdemarFB/)\
🎥 Follow me on [TikTok](https://www.tiktok.com/@heyvaldemar)\
💻 Follow me on [LinkedIn](https://www.linkedin.com/in/heyvaldemar/)\
🐈 Follow me on [GitHub](https://github.com/heyvaldemar)

# Communication
👾 Chat with IT pros on [Discord](https://discord.gg/AJQGCCBcqf)\
📧 Reach me at ask@sre.gg

# Give Thanks
💎 Support on [GitHub](https://github.com/sponsors/heyValdemar)\
🏆 Support on [Patreon](https://www.patreon.com/heyValdemar)\
🥤 Support on [BuyMeaCoffee](https://www.buymeacoffee.com/heyValdemar)\
🍪 Support on [Ko-fi](https://ko-fi.com/heyValdemar)\
💖 Support on [PayPal](https://www.paypal.com/paypalme/heyValdemarCOM)
