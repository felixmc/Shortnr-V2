# Shortnr


## Purpose

Url-shortening service with a client API for shortening URLs as well as analytics gathering capabilities.


## Glossary

*service* - an instance of the shortnr service

*client* - a person or program that uses the shortnr service to generate shortened urls

*user* - a person or program that follows a link handled by the service

*url code* - a random string mapped to a URL


## Features

- client REST API for shortened URLs CRUD
- analytics collection for users (user agent, ip, referer, etc)
- modular components


## Components

-- http server (connect-like)
	-- client router (optional)
		-- authentication middleware (optional)
		-- other middleware (rate limiting, client analytics, etc, optional)
		-- REST API
			--> URL persistance driver (read, write)
	-- user router
		-- analyics middleware (optional)
			-- persistance driver
		-- other middleware (user filtering for whatever reason, etc)
		-- URL mapper
			--> URL persistance driver (read)


## Modularity

Shortnr should allow the following features to be modular

- analytics
	- persistance (database driver for storing analytics, for example mongo, mysql, fs)
	- data params (determines what datapoints are collected from each request)
- url persistance (database drivers for storing and retrieving urls and url codes)
- client authentication
- generic connect middleware for both clients and users
- logger


## Customization

Options that should be customizable.

- domain whitelist and/or blacklist for submitted client URLs
- url codes
	- case sensitivity
	- length
	- charset/ranges
- virtual hosts
- 301 vs 302 redirection
- cookie or no cookie
- client white/black list
- spider handling (how to handle google/facebook/etc trying to figure out the real url. can maybe check based on user agent?)
- valid url pattern
- allow short URLs to be shortened
- rate limits
- 

### User tracking

Set cookie on redirect to keep track of users between sessions (might not work with all browsers)
