# spotish

download saved tracks on spotify;

## install

install spotish with pip:

    pip install spotish

## usage

to use spotish, you need to create a spotify application:

1.  go to <https://developer.spotify.com/dashboard/applications> and log in;

2.  click *create a client id*;

3.  fill in any name and description, then choose *desktop app*;

4.  on next page, when asked *are you developing a commercial integration?*,
    choose *no*;

5.  on next page, tick all boxes and click *submit*;

6.  now the app is created; the app page lists its client id and client secret,
    which will be used when you run spotish; we also need a redirect uri, so
    click *edit settings*;

7.  add `http://localhost/callback/` in *redirect uris*; this uri will be used
    when you run spotish;

8.  click *save*;

now we have a spotify username, a client id, a client secret and a redirect uri;

to download saved tracks into the default `tracks` dir:

    spotish --user {username} \
        --client-id {client_id} --client-secret {client_secret} \
        --redirect-uri {redirect_uri}

on first run, this will open a web browser and ask you to enter the redirect uri
to authenticate; simply follow the instructions; this will generate a hidden
cache file named `.cache-<username>` in current dir, containing spotify web api
access token; later runs of spotish dont need authentication until the access
token expires;

tracks are organized by their albums; both albums and tracks are named after
their uuids; an album uuid contains total tracks in album, album uri and album
name; a track uuid contains track number within the album, track uri and track
name; album and track uris already guarantee uniqueness; however, uuids contain
more information and are easier to visualize; by using uuids, tracks within an
album are automatically sorted by their track numbers, which looks very nice;

to download saved tracks with more complete metadata and helpful progress text:

    spotish --user {username} \
        --client-id {client_id} --client-secret {client_secret} \
        --redirect-uri {redirect_uri} \
        --output {dir} \
        --album-image --track-preview \
        --verbose

spotish offers the following options:

-   to specify output dir:

        --output {dir}

-   to download album image:

        --album-image

-   to download track preview:

        --track-preview

-   to dump raw json response:

        --debug

-   to display more information:

        --verbose

## depend

spotish depends on:

-   [spotipy](https://github.com/plamere/spotipy);

## license

Copyright (c) 2018 Cyker Way

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation, either version 3 of the License, or (at your option) any later
version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with
this program.  If not, see <https://www.gnu.org/licenses/>.

