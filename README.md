
Fork of visibilityspots/smashing. Some of the newer commits did break our builds, and since
there is no versioning the only chance I saw was forking the complete project. And yes,
it had to be public repositories (not my choice).


# smashing
Run [smashing](https://github.com/Smashing/smashing) in a [Docker](http://docker.io/) container.

Originated from: [frvi/dashing](https://registry.hub.docker.com/u/frvi/dashing/)

Link: [stummb/smashing](https://registry.hub.docker.com/u/stummb/smashing/)

[![Anchore Image Overview](https://anchore.io/service/badges/image/316adb3394c43dd1caf39ccf4d9799bf9bcee549cb3aa77eee9f46e24a30ceb3)](https://anchore.io/image/dockerhub/stummb%2Fsmashing%3Alatest)


## Run
```docker run -d -p 8080:3030 stummb/smashing```

And point your browser to [http://localhost:8080/](http://localhost:8080/).


## Configuration
### Custom smashing port
If you want smashing to use a custom port inside the container, e g 8080, use the environment variable `$PORT`:

```docker run -d -e PORT=8080 -p 80:8080 stummb/smashing```

### Dashboards
To provide a custom dashboard, use container volume **/dashboards**:

```docker run -v=/my/custom/dashboards:/dashboards -d -p 8080:3030 stummb/smashing```

(*Don't forget to also provide the layout.erb*)

### Jobs
To provide custom jobs, use container volume **/jobs**:

```docker run -v=/my/cool/job:/jobs -d -p 8080:3030 stummb/smashing```

### Widgets
To install custom widgets supply the gist IDs of the widgets as an environment variable:

```docker run -d -e WIDGETS=5641535 -p 8080:3030 stummb/smashing```

This example will install the [Random Aww](https://gist.github.com/chelsea/5641535) widget
before starting smashing. Multiple widgets can be supplied.

Also you can use local custom widgets

```docker run -v=/my/cool/widgets:/widgets -d -p 8080:3030 stummb/smashing```


### Gems
To install gems, supply the gem name(s) as an environment variable:

```docker run -d -e GEMS=instagram -e WIDGETS=5278790 -p 8080:3030 stummb/smashing```

This example installs the [Instagram photos by location](https://gist.github.com/mjamieson/5278790) widget,
which depends on the instagram gem. Multiple gems and widgets can be supplied like so:

```docker run -d -e GEMS="mysql instagram" -e WIDGETS=5278790 -p 8080:3030 stummb/smashing```

### Public (favicon, 404)
To provide custom 404 and favicon, use container volume **/public**.

### Configuration File
The configuration file ```config.ru``` is available on volume */config*.

Edit this file to change your API key, to add authentication and more.

### lib volume
The smashing lib dir is available on volume */lib-smashing*.

## Thanks
- [@mattgruter](https://github.com/mattgruter), awsome contributions!
- [@rowanu](https://github.com/rowanu), [Hotness Widget](https://gist.github.com/rowanu/6246149).
- [@munkius](https://github.com/munkius), [fork](https://gist.github.com/munkius/9209839) of Hotness Widget.
- [@chelsea](https://github.com/chelsea), [Random Aww](https://gist.github.com/chelsea/5641535).

## TODO:
- [x] Use official Ruby image from Docker hub. (Thank you [@bemehow](https://github.com/bemehow))

## License
Distributed under the MIT license
