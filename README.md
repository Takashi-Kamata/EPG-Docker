# EPG Automatic Fetch Container

I made Docker containers to automatically pull and publish EPG using [iptv-org](https://github.com/iptv-org/iptv)'s [EPG](https://github.com/iptv-org/epg) repo.

I have a dockerized Live-TV Jellyfin setup and this docker-compose is used to pull channel information from the internet and storing it as XML file.

Just copy the frontend link "http://local-ip:4000/guide.xml" into TV Guide Data Providers -> XMLTV.

## Design

Two services 'Frontend' and 'Backend' are containerized.


Frontend is responsible for git cloning the EPG repo and initializing the npx serve for external access. It uses the 'epg' volume to share the repo with backend container.

Backend rides on the same volume as frontend to reduce duplicating files. It fetches the channel information with cron scheduler. 

## Installation

At the parent directory (where compose.yml sits), run:

```bash
sudo docker compose up --build -d
```

## Usage

```bash
# Change the --site flag link for you IP-TV region
# Change the --cron flag to adjust fetch time (every 6h)
CMD ["npm", "run", "grab", "--", "--site=tvguide.myjcom.jp", "--cron=* */6 * * *"]

```

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](LICENSE)