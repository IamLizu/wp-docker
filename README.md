# WordPress with Docker

This makes local WordPress development easy by spinning up a website using WordPress, MySQL and PhpMyAdmin.

### Getting started

---

1. [Install docker in your system](https://docs.docker.com/get-docker/).
2. Pull this repository.
3. Create `.env` from `.env-sample`.
4. Set the required values in `.env`.
5. Execute `docker-compose up -d` from a terminal inside the directory.

## Key Commands

---

`docker-compose down` to stop the container.  
`docker-compose build` to rebuild the container.

See this for further reference on `docker-compose`, https://docs.docker.com/compose/reference/

## Extend

---

If you want to install themes or plugins during the website setup, edit the `docker-compose.yml` file and map the files in the WordPress' volume.

For example, if I were to install Divi, which is a theme, I would add the following,  
`- ./themes/Divi:/var/www/html/wp-content/themes/Divi`

And if I were to install Sucuri Scanner, which is a plugin, I would add,

`- ./plugins/sucuri-scanner:/var/www/html/wp-content/plugins/sucuri-scanner`

Here, `./themes/` and `./plugins/` are local directories where you I would paste the files. You can create different directories on local to store the files. However, rest of the part for the mapping needs follow the directory structure of WordPress.

You will find commented out plugin, theme installation in the `docker-compose.yml`, you can remove those, add your own, or edit those. I left those as is because my frequent use of those.

## Acknowledgement

---

My [`docker-compose.yml`](https://github.com/IamLizu/wp-docker/blob/main/docker-compose.yml) is an improved version of [Brad's `docker-compose.yml` for WordPress](https://gist.github.com/bradtraversy/faa8de544c62eef3f31de406982f1d42). (Kudos to [Brad Traversy](https://github.com/bradtraversy/) for his contributions to the community.)

As of creating this repo, if you use Brad's version of the file, you may face database connection issue if your database name is anything else that `wordpress`.
