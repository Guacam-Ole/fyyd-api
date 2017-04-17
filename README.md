# fyyd api

Documentations version: 0.1

---

This is the initial documentation for the API to fyyd, the podcast search engine, directory and slow cooker.

Take my apologies for this simple markdown, I tried to use something more fancy, but I took an arrow to my knee.

---

## Endpoint for version 0.2

https://api.fyyd.de/0.2/

always prefix this for every request or else you'll end up in version 0.1 which is mostly different from 0.2.

---

## Table of contents

1. [Preface](#preface)
2. [Account](#account)
3. [User](#user)
4. [Action](#action)
5. [Podcast](#podcast)
6. [Episode](#episode)
7. [Curation](#curation)
8. [Collection](#collection)

---

## Preface

Podcasts and their metadata always has been a fascinating subject for me. So much data, so few approaches to collect and bring it to good use.

Now it's 2017 and there are a few (I know of three, maybe four) more or less experimental projects to work with this gigantic loads of data. One of that projects is fyyd, my attempt to create a 

* podcast search engine
* podcast directory
* podcast recommendation system

fyyd is a freetime project, that get's some love now and then. The progress is as fast as I can afford some free time beside family, job and whatever one has to do. 

As I started fyyd, I knew that an API would be crucial for this project to escape the scope of just a webpage and to find more stunning ways to do whatever one can do with that data. As always: The crowd will find a way to use the data you would never have dreamed of.

Version 0.1 of that API found it's way to a small group of developers, leading into the development of [Skoon](https://skoon.stefantrauth.de), an iOS-App to curate podcast's episodes directly from some podcatchers and the integration of fyyd into [podcat](http://www.podc.at/), a lovely designed podcatcher that pleasantly differs from most machine like user interfaces. 

Version 0.1 had its problems and was a rush job. Thanks to Jeanette and Stefan here and now you see the documentation for version 0.2, that at the moment has no additional features, but recieved a rewrite to be more logical and safe.



Thanks to all who helped, will help and contribute to this small project.

---



# Account

Requests for /account always refer to the user identified by the accesstoken.



### [GET /account/info]

#### Description 

Returns general information about the account

#### Parameters

none

#### Response

	{
		"status": 1,
		"msg": "ok",
		"meta": {
			"API_INFO": {
				"API_VERSION": 0.2
			}
		},
		"data": {
			"nick": "your-nick",
			"id": 42,
			"fullname": "Jon Doe",
			"bio": "This is me!",
			"url": "https:\/\/fyyd.de\/",
			"layoutImageURL": "https:\/\/img.fyyd.de\/user\/layout\/42.jpg",
			"thumbImageURL": "https:\/\/img.fyyd.de\/user\/thumbs\/42.png",
			"microImageURL": "https:\/\/img.fyyd.de\/user\/micro\/42.png"
		}
	}



### [GET /account/curations]

#### Description

Returns this account's curations. Includes non-public curations as well.

#### Parameters

none

#### Response

```
{
    "status": 1,
    "msg": "ok",
    "meta": {
        "API_INFO": {
            "API_VERSION": 0.2
        }
    },
    "data": [
        {
            "title": "Retro Computing",
            "id": 1099,
            "description": "Alles \u00fcber Rechner, f\u00fcr die es garantiert keine Garantie mehr gibt.",
            "layoutImageURL": "https:\/\/img.fyyd.de\/curation\/layout\/1099.jpg",
            "thumbImageURL": "https:\/\/img.fyyd.de\/curation\/thumbs\/1099.png",
            "microImageURL": "https:\/\/img.fyyd.de\/curation\/micro\/1099.png",
            "public": 0,
            "slug": "retro-computing",
            "url": "https:\/\/fyyd.de\/user\/eazy\/curation\/retro-computing",
            "xmlURL": "https:\/\/feeds.fyyd.de\/eazy\/retro-computing"
        },
        {
            "title": "Netzpolitik",
            "id": 623,
            "description": "Vorsicht, k\u00f6nnte Spuren von Netzpolitik enthalten!",
            "layoutImageURL": "https:\/\/img.fyyd.de\/curation\/layout\/623.jpg",
            "thumbImageURL": "https:\/\/img.fyyd.de\/curation\/thumbs\/623.png",
            "microImageURL": "https:\/\/img.fyyd.de\/curation\/micro\/623.png",
            "public": 1,
            "slug": "netzpolitik",
            "url": "https:\/\/fyyd.de\/user\/eazy\/curation\/netzpolitik",
            "xmlURL": "https:\/\/feeds.fyyd.de\/eazy\/netzpolitik"
        },
        {
            "title": "Podcasting",
            "id": 586,
            "description": "Alles \u00fcber das Podcasting",
            "layoutImageURL": "https:\/\/img.fyyd.de\/curation\/layout\/586.jpg",
            "thumbImageURL": "https:\/\/img.fyyd.de\/curation\/thumbs\/586.png",
            "microImageURL": "https:\/\/img.fyyd.de\/curation\/micro\/586.png",
            "public": 1,
            "slug": "podcasting",
            "url": "https:\/\/fyyd.de\/user\/eazy\/curation\/podcasting",
            "xmlURL": "https:\/\/feeds.fyyd.de\/eazy\/podcasting"
        }
 
    ]
}
```



### [GET /account/collections]

#### Description

Returns this account's collections.

#### Parameters

none

#### Response

```
{
    "status": 1,
    "msg": "ok",
    "meta": {
        "API_INFO": {
            "API_VERSION": 0.2
        }
    },
    "data": [
        {
            "title": "Netzpolitik",
            "id": 1,
            "description": "(Netz)politische Podcasts",
            "layoutImageURL": "https:\/\/img.fyyd.de\/collection\/layout\/1.jpg",
            "thumbImageURL": "https:\/\/img.fyyd.de\/collection\/thumbs\/1.png",
            "microImageURL": "https:\/\/img.fyyd.de\/collection\/micro\/1.png",
            "slug": "netzpolitik",
            "url": "https:\/\/fyyd.de\/user\/eazy\/collection\/netzpolitik"
        },
        {
            "title": "Gamechanger",
            "id": 8,
            "description": "",
            "layoutImageURL": "https:\/\/img.fyyd.de\/collection\/layout\/8.jpg",
            "thumbImageURL": "https:\/\/img.fyyd.de\/collection\/thumbs\/8.png",
            "microImageURL": "https:\/\/img.fyyd.de\/collection\/micro\/8.png",
            "slug": "gamechanger",
            "url": "https:\/\/fyyd.de\/user\/eazy\/collection\/gamechanger"
        },
        {
            "title": "Lieblingspodcasts",
            "id": 11,
            "description": "Was ich so mit auf die Insel nehmen w\u00fcrde..",
            "layoutImageURL": "https:\/\/img.fyyd.de\/collection\/layout\/11.jpg",
            "thumbImageURL": "https:\/\/img.fyyd.de\/collection\/thumbs\/11.png",
            "microImageURL": "https:\/\/img.fyyd.de\/collection\/micro\/11.png",
            "slug": "lieblingspodcasts",
            "url": "https:\/\/fyyd.de\/user\/eazy\/collection\/lieblingspodcasts"
        }
    ]
}
```

------



# User

Gets public available information about a registered account at fyyd



### [GET /user/{id}]

#### Description

Retrieves the accounts profile information

#### Parameters

* **id (required, int)** the users account id

#### Response

    {
      "status": 1,
      "msg": "ok",
      "meta": {
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
      "data": {
          "nick": "eazy",
          "id": 42,
          "fullname": "John Doe",
          "bio": "This is me!",
          "url": "https:\/\/fyyd.de\/",
          "layoutImageURL": "https:\/\/img.fyyd.de\/user\/layout\/42.jpg",
          "thumbImageURL": "https:\/\/img.fyyd.de\/user\/thumbs\/42.png",
          "microImageURL": "https:\/\/img.fyyd.de\/user\/micro\/42.png"
      }
    }


### [GET /user/{id}/curations[/episodes]]

#### Description

Retrieves the curations maintained by the given user. You may append /episodes to also get the content of this curations.

#### Parameters

- **id (required, int)** the users account id

#### Response

    {
      "status": 1,
      "msg": "ok",
      "meta": {
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
      "data": [
          {
              "title": "Netzpolitik",
              "id": 623,
              "description": "Vorsicht, k\u00f6nnte Spuren von Netzpolitik enthalten!",
              "layoutImageURL": "https:\/\/img.fyyd.de\/curation\/layout\/623.jpg",
              "thumbImageURL": "https:\/\/img.fyyd.de\/curation\/thumbs\/623.png",
              "microImageURL": "https:\/\/img.fyyd.de\/curation\/micro\/623.png",
              "public": 1,
              "slug": "netzpolitik",
              "url": "https:\/\/fyyd.de\/user\/eazy\/curation\/netzpolitik",
              "xmlURL": "https:\/\/feeds.fyyd.de\/eazy\/netzpolitik"
          },
          {
              "title": "Podcasting",
              "id": 586,
              "description": "Alles \u00fcber das Podcasting",
              "layoutImageURL": "https:\/\/img.fyyd.de\/curation\/layout\/586.jpg",
              "thumbImageURL": "https:\/\/img.fyyd.de\/curation\/thumbs\/586.png",
              "microImageURL": "https:\/\/img.fyyd.de\/curation\/micro\/586.png",
              "public": 1,
              "slug": "podcasting",
              "url": "https:\/\/fyyd.de\/user\/eazy\/curation\/podcasting",
              "xmlURL": "https:\/\/feeds.fyyd.de\/eazy\/podcasting"
          }
      ]
    }


### [GET /user/{id}/collections[/podcasts]]

#### Description

Retrieves the collections maintained by the given user. You may append /podcasts to also get the content of this collections.

#### Parameters

- **id (required, int)** the users account id

#### Response

    {
      "status": 1,
      "msg": "ok",
      "meta": {
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
      "data": [
          {
              "title": "Netzpolitik",
              "id": 1,
              "description": "(Netz)politische Podcasts",
              "layoutImageURL": "https:\/\/img.fyyd.de\/collection\/layout\/1.jpg",
              "thumbImageURL": "https:\/\/img.fyyd.de\/collection\/thumbs\/1.png",
              "microImageURL": "https:\/\/img.fyyd.de\/collection\/micro\/1.png",
              "slug": "netzpolitik",
              "url": "https:\/\/fyyd.de\/user\/eazy\/collection\/netzpolitik"
          },
          {
              "title": "Gamechanger",
              "id": 8,
              "description": "",
              "layoutImageURL": "https:\/\/img.fyyd.de\/collection\/layout\/8.jpg",
              "thumbImageURL": "https:\/\/img.fyyd.de\/collection\/thumbs\/8.png",
              "microImageURL": "https:\/\/img.fyyd.de\/collection\/micro\/8.png",
              "slug": "gamechanger",
              "url": "https:\/\/fyyd.de\/user\/eazy\/collection\/gamechanger"
          }
      ]
    }
---



# Action

This is the actions API to fyyd. It's a more or less formfree key-value-store.

Requests for /action always refer to the user identified by the accesstoken.

### [POST /action]

#### Description

Saves an action for the authorized user.

The action always referes to an object inside fyyd's database, which may be:

* an episode
* a podcast
* a curation
* a colleciton
* a user

The action itself is represented by a string you may choose freely. Some of these actions will be used in future features of fyyd. This is not implemented at the time this documentation is written. 

#### Parameters

+ **object_id (required, int)** the id of the object
+ **object_type (required, string)** the type of the object. episode, podcast, curation, collection, user
+ **action (required, string)** a free to choose action
+ **metadata (optional, string)** further data you'd like to associate to this action

#### Response

Returns 204 - No Content

---



# Podcast

Retrieves information about a podcast

### [GET /podcast/{id}[/episodes[/{page}[/{count}]]]]

#### Description

Gets information about the podcast with id {id}. You may retrieve the episodes by appending /episodes.

Additionally you can address the resultset with {page} and {count}.

#### Parameters

- **id (required, int)** the Podcast's id
- **page (optional, int)** the page you want to address, default: 0
- **count (optional,int)** the pages size, default: 50

#### Response

    {
      "status": 1,
      "msg": "ok",
      "meta": {
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
      "data": {
          "title": "Schall und Rauch",
          "id": 64,
          "xmlURL": "http:\/\/schallrauch.hoersuppe.de\/sur\/m4a",
          "htmlURL": "http:\/\/schallrauch.hoersuppe.de\/sur\/show",
          "imgURL": "http:\/\/schallrauch.hoersuppe.de\/feedimages\/itunes1400.png",
          "status": 399,
          "slug": "schall-und-rauch",
          "layoutImageURL": "https:\/\/img.fyyd.de\/pd\/layout\/64.jpg",
          "thumbImageURL": "https:\/\/img.fyyd.de\/pd\/thumbs\/64.png",
          "microImageURL": "https:\/\/img.fyyd.de\/pd\/micro\/64.png",
          "language": "de",
          "lastpoll": "2017-04-17 14:42:41",
          "generator": "firtz podcast publisher v2.0",
          "user_id": 1000,
          "categories": 52,
          "lastpub": "2016-01-08 21:15:22",
          "rank": 22,
          "url_fyyd": "https:\/\/fyyd.de\/podcast\/64",
          "description": "Alexander und Christian, zwei mittelreife Fr\u00fcchte der 70er, sozialisiert in den 80ern ver\u00f6ffentlichen ihre monatlichen Schw\u00e4tzchen auf der Parkbank.",
          "subtitle": "Zwei Opas erz\u00e4hlen vom Krieg",
          "episodes": [
              {
                  "title": "Stasi, Sherlock und die ARD",
                  "id": 1742,
                  "guid": "sur-sur022",
                  "url": "http:\/\/schallrauch.hoersuppe.de\/sur\/show\/sur022",
                  "enclosure": "http:\/\/cdn.podseed.org\/schallundrauch\/sur022.m4a",
                  "podcast_id": 64,
                  "imgURL": "http:\/\/schallrauch.hoersuppe.de\/feedimages\/itunes1400.png",
                  "pubdate": "2016-01-08 21:15:22",
                  "duration": 5579,
                  "url_fyyd": "https:\/\/fyyd.de\/episode\/1742",
                  "description": "<p>Alexander erz\u00e4hlt von seinen Eindr\u00fccken beim Besuch der BStU, war dar\u00fcber hinaus in London und macht mir die Nase lang, weil er dort die aktuelle Folge Sherlock schon geschaut hat. Im Hotel. So ein Hund!<\/p>\n\n<p>Daf\u00fcr aber hat Deutschland durchaus etwas zu bieten im Bereich der Serien, man sollte nur nicht unbedingt beim Tatort suchen. Alexander rezitiert Schweiger, was dann schnell das Ende der Folge einl\u00e4utet&hellip;<\/p>\n"
              }
          ]
       }
    }


### [POST /podcast/{id}/action/{action}]

### Description

Performes an action to a podcast owned by you (see claim-button on every podcast page).

At the moment, 'check' is the only action to perform. This triggers an update within the next poll cycle.

#### Parameters

- **id (required, int)** the Podcast's id
- **action (required, string)** the action to perform:
  * **check** 

#### Response

returns a 204: No Content



### [GET /podcasts[/{page}[/{count}]]]]

#### Description

Gets information about all podcasts within fyyd.

Additionally you can address the resultset with {page} and {count}. 

Please note that this request is the plural form of podcast, podcasts  ;-)

#### Parameters

- **id (required, int)** the Podcast's id
- **page (optional, int)** the page you want to address, default: 0
- **count (optional,int)** the pages size, default: 50

 #### Response

The response includes data about the pagination.

    {
      "status": 1,
      "msg": "ok",
      "meta": {
          "paging": {
              "count": 2,
              "page": 0,
              "first_page": 0,
              "last_page": 7094,
              "next_page": 1,
              "prev_page": null
          },
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
      "data": [
          {
              "title": "Freakonomics Radio",
              "id": 1,
              "xmlURL": "http:\/\/feeds.feedburner.com\/freakonomicsradio",
              "htmlURL": "http:\/\/www.wnyc.org\/articles\/freakonomics-podcast",
              "imgURL": "https:\/\/media2.wnyc.org\/i\/1400\/1400\/l\/80\/1\/wn16_wnycstudios_freakonomics-rev3.png",
              "status": 390,
              "slug": "freakonomics-radio",
              "layoutImageURL": "https:\/\/img.fyyd.de\/pd\/layout\/1.jpg",
              "thumbImageURL": "https:\/\/img.fyyd.de\/pd\/thumbs\/1.png",
              "microImageURL": "https:\/\/img.fyyd.de\/pd\/micro\/1.png",
              "language": "en",
              "lastpoll": "2017-04-16 00:34:49",
              "generator": null,
              "user_id": null,
              "categories": 52,
              "lastpub": "2017-03-16 04:00:00",
              "rank": 1,
              "url_fyyd": "https:\/\/fyyd.de\/podcast\/1",
              "description": "Have fun discovering the hidden side of everything with host Stephen J. Dubner, co-author of the best-selling \"Freakonomics\u201d books. Each week, hear surprising conversations that explore the riddles of everyday life and the weird wrinkles of human nature\u2014from cheating and crime to parenting and sports. Dubner talks with Nobel laureates and provocateurs, social scientists and entrepreneurs \u2014 and his \u201cFreakonomics\u201d co-author Steve Levitt. After just a few episodes, this podcast will have you too thinking like a Freak. Produced by WNYC Studios, home of other great podcasts such as \u201cRadiolab,\" \"Death, Sex & Money,\" and \"On the Media.\" ",
              "subtitle": "Have fun discovering the hidden side of everything with host Stephen J. Dubner, co-author of the best-selling \"Freakonomics\u201d books. Each week, hear surprising conversations that explore the riddles of everyday life and the weird wrinkles of human nature\u2014f"
          },
          {
              "title": "Skeptoid",
              "id": 3,
              "xmlURL": "http:\/\/skeptoid.com\/podcast.xml",
              "htmlURL": "https:\/\/skeptoid.com",
              "imgURL": "http:\/\/skeptoid.com\/images\/1500b.jpg",
              "status": 304,
              "slug": "skeptoid",
              "layoutImageURL": "https:\/\/img.fyyd.de\/pd\/layout\/3.jpg",
              "thumbImageURL": "https:\/\/img.fyyd.de\/pd\/thumbs\/3.png",
              "microImageURL": "https:\/\/img.fyyd.de\/pd\/micro\/3.png",
              "language": "en",
              "lastpoll": "2017-04-17 02:39:44",
              "generator": null,
              "user_id": null,
              "categories": "48,51,50",
              "lastpub": "2017-04-11 02:00:00",
              "rank": 1,
              "url_fyyd": "https:\/\/fyyd.de\/podcast\/3",
              "description": "Since 2006, the weekly Skeptoid podcast has been taking on all the most popular myths and revealing the true science, true history, and true lessons we can learn from each. Free subscribers get the most recent 50 episodes, premium subscribers (skeptoid.com) can access the full archive, all ad-free.",
              "subtitle": "A weekly look at the true facts behind urban legends and stories you've probably heard."
          }
      ]
    }


Additionally links inside the header are provided:

`Link: <https://api.fyyd.de/0.2/podcasts/1/2>; rel="next", <https://api.fyyd.de/0.2/podcasts/0/2>; rel="first", <https://api.fyyd.de/0.2/podcasts/7094/2>; rel="last"`



### [GET /categories]

### Description

Gets the complete categories tree

#### Parameters

none

#### Response	

    {
      "status": 1,
      "msg": "ok",
      "meta": {
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
      "data": [
          {
              "id": 1,
              "slug": "arts",
              "name": "Arts",
              "name_de": "Kunst",
              "subcategories": [
                  {
                      "id": 2,
                      "slug": "design",
                      "name": "Design",
                      "name_de": "Design"
                  },
                  {
                      "id": 3,
                      "slug": "fashion-beauty",
                      "name": "Fashion & Beauty",
                      "name_de": "Mode & Sch\u00f6nheit"
                  },
                  {
                      "id": 4,
                      "slug": "food",
                      "name": "Food",
                      "name_de": "Essen"
                  },
                  {
                      "id": 5,
                      "slug": "literature",
                      "name": "Literature",
                      "name_de": "Literatur"
                  },
                  {
                      "id": 6,
                      "slug": "performing-arts",
                      "name": "Performing Arts",
                      "name_de": "Darstellende K\u00fcnste"
                  },
                  {
                      "id": 7,
                      "slug": "visual-arts",
                      "name": "Visual Arts",
                      "name_de": "Bildende K\u00fcnste"
                  }
              ]
          },
          {
              "id": 8,
              "slug": "business",
              "name": "Business",
              "name_de": "Wirtschaft",
              "subcategories": [
                  {
                      "id": 9,
                      "slug": "business-news",
                      "name": "Business News",
                      "name_de": "Wirtschaftsnachrichten"
                  },
                  {
                      "id": 10,
                      "slug": "careers",
                      "name": "Careers",
                      "name_de": "Karriere"
                  },
                  {
                      "id": 11,
                      "slug": "investing",
                      "name": "Investing",
                      "name_de": "Geldanlage"
                  },
                  {
                      "id": 12,
                      "slug": "management-marketing",
                      "name": "Management & Marketing",
                      "name_de": "Management & Markteting"
                  },
                  {
                      "id": 13,
                      "slug": "shopping",
                      "name": "Shopping",
                      "name_de": "Shopping"
                  }
              ]
          },
          {
              "id": 14,
              "slug": "comedy",
              "name": "Comedy",
              "name_de": "Kom\u00f6dien",
              "subcategories": []
          }
         ]
       ]
     }



### [GET /category/{id}[/{page}[/{count}]]]

### Description

Retrieves the podcasts inside the specified category. The categories system referres to Apple's iTunes Categories. Categories not in Apple's specification are ignored on import.

#### Parameters

* **id (required, int)** the category's id (see /categories)
* **page (optional, int)** the page you want to address, default: 0
* **count (optional,int)** the pages size, default: 50

#### Response

    {

     "status": 1,
      "msg": "ok",
      "meta": {
          "paging": {
              "count": 2,
              "page": 0,
              "first_page": 0,
              "last_page": 117,
              "next_page": 1,
              "prev_page": null
          },
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
      "data": {
          "category": {
              "id": 61,
              "slug": "professional",
              "title": "Professional",
              "url": "https:\/\/fyyd.de\/discover\/cat\/professional\/0"
          },
          "parent": {
              "id": 57,
              "slug": "sports-recreation",
              "title": "Sports & Recreation",
              "url": "https:\/\/fyyd.de\/discover\/cat\/sports-recreation\/0"
          },
          "podcasts": [
              {
                  "title": "vollraute - der gladbach podcast mit der raute im herzen -",
                  "id": 170,
                  "xmlURL": "http:\/\/feedpress.me\/vollrautepodcast",
                  "htmlURL": "http:\/\/vollraute.de",
                  "imgURL": "http:\/\/vollraute.de\/wp-content\/cache\/podlove\/5a\/cc055669c606ec882f928be09be530\/vollraute-der-gladbach-podcast-mit-der-raute-im-herzen_original.png",
                  "status": 390,
                  "slug": "vollraute-der-gladbach-podcast-mit-der-raute-im-herzen",
                  "layoutImageURL": "https:\/\/img.fyyd.de\/pd\/layout\/170.jpg",
                  "thumbImageURL": "https:\/\/img.fyyd.de\/pd\/thumbs\/170.png",
                  "microImageURL": "https:\/\/img.fyyd.de\/pd\/micro\/170.png",
                  "language": "de",
                  "lastpoll": "2017-04-16 00:36:11",
                  "generator": "Podlove Podcast Publisher v2.4.1",
                  "user_id": null,
                  "categories": "57,21,61",
                  "lastpub": "2017-04-11 21:14:53",
                  "rank": 1,
                  "url_fyyd": "https:\/\/fyyd.de\/podcast\/170",
                  "description": "Ein Podcast \u00fcber die Borussia aus M\u00f6nchengladbach.\nNie neutral, sondern immer durch die Vereinsbrille.",
                  "subtitle": "Ein Podcast \u00fcber die Borussia aus M\u00f6nchengladbach"
              },
              {
                  "title": "Collinas Erben",
                  "id": 296,
                  "xmlURL": "http:\/\/fokus-fussball.de\/feed\/mp3\/",
                  "htmlURL": "http:\/\/fokus-fussball.de",
                  "imgURL": "http:\/\/fokus-fussball.de\/wp-content\/cache\/podlove\/5f\/716d5e4a7909b9b87b75a456524d89\/collinas-erben_original.jpg",
                  "status": 304,
                  "slug": "collinas-erben",
                  "layoutImageURL": "https:\/\/img.fyyd.de\/pd\/layout\/296.jpg",
                  "thumbImageURL": "https:\/\/img.fyyd.de\/pd\/thumbs\/296.png",
                  "microImageURL": "https:\/\/img.fyyd.de\/pd\/micro\/296.png",
                  "language": "de",
                  "lastpoll": "2017-04-17 16:12:25",
                  "generator": "Podlove Podcast Publisher v2.3.8",
                  "user_id": null,
                  "categories": "57,61,58",
                  "lastpub": "2016-11-15 08:53:35",
                  "rank": 10,
                  "url_fyyd": "https:\/\/fyyd.de\/podcast\/296",
                  "description": "Fu\u00dfball ist ein einfaches Spiel \u2013 deshalb ist es so erfolgreich: Der Ball ist rund. Das Spiel dauert um die 90 Minuten.\n\nProblematisch wird es nur, wenn Sonderf\u00e4lle auftreten. Wenn ein Spieler pl\u00f6tzlich mit nacktem Oberk\u00f6rper auf den Zaun springt, wenn ein Engl\u00e4nder doch mal mit einem Wembley-Tor trifft oder wenn auch nach der zigsten Wiederholung nicht klar ist, ob es ein Foul in der 88. Minute war und ob es im oder vor dem Strafraum passierte.\n\nDer Schiedsrichter-Podcast Collinas Erben m\u00f6chte f\u00fcr mehr Fachwissen auf den Trib\u00fcnen und an den Empfangsger\u00e4ten sorgen. Alex Feuerherdt und Klaas Reese sprechen \u00fcber das Schiedsrichterwesen im Allgemeinen und die Spielregeln im Speziellen.",
                  "subtitle": "Der Schiedsrichter-Podcast"
              }
          ]
      }
    }





---



# Episode

Request to retrieve an episode's information

### [GET /episode/{id}]

### Description

Returns information about a single episode

#### Parameters

- **id (required, int)** the episode's id

#### Response

    {
      "status": 1,
      "msg": "ok",
      "meta": {
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
       "data": {
            "title": "Space Hulk (Stay Forever, Folge 33)",
            "id": 42,
            "guid": "796a53669cb29b0504fdd4f0a3f9a41d",
            "url": "http:\/\/kaliban.podspot.de\/files\/Stay_Forever_Ep33_Space_Hulk.mp3",
            "enclosure": "http:\/\/kaliban.podspot.de\/files\/Stay_Forever_Ep33_Space_Hulk.mp3",
            "podcast_id": 5,
            "imgURL": "",
            "pubdate": "2014-03-06 18:10:30",
            "duration": null,
            "url_fyyd": "https:\/\/fyyd.de\/episode\/42",
            "description": "Christian hasst Space Hulk, Gunnar liebt es. Fight!"
        }
    }
---



# Curations

All about Curations inside fyyd. Retrieve and set.

### [GET /curation/{id}[/episodes]]

### Description

Returns information about a single curation, given the curation's id. May append episodes, not paged at the moment.

#### Parameters

- **id (required, int)** the curation's id

#### Response

    {

      "status": 1,
      "msg": "ok",
      "meta": {
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
      "data": {
          "title": "Testfeed",
          "id": 601,
          "description": "nur ein Testfeed",
          "layoutImageURL": "https:\/\/fyyd.de\/images\/curation300.png",
          "thumbImageURL": "https:\/\/fyyd.de\/images\/curation80.png",
          "microImageURL": "https:\/\/fyyd.de\/images\/curation20.png",
          "public": 1,
          "slug": "testfeed",
          "user_id": 1000,
          "url": "https:\/\/fyyd.de\/user\/eazy\/curation\/testfeed",
          "xmlURL": "https:\/\/feeds.fyyd.de\/eazy\/testfeed",
          "episodes": [
              {
                  "title": "A!195 \u2013 Raussismus",
                  "id": 1662345,
                  "guid": "podlove-2017-04-14t12:27:42+00:00-56a19c3a4209a8d",
                  "url": "https:\/\/aufwachen-podcast.de\/2017\/04\/14\/a195-raussismus\/",
                  "enclosure": "https:\/\/aufwachen-podcast.de\/podlove\/file\/3244\/s\/feed\/c\/itunes\/195raussismus.m4a",
                  "podcast_id": 95,
                  "imgURL": "",
                  "pubdate": "2017-04-14 15:05:11",
                  "duration": 16018,
                  "favedDate": "2017-04-17 16:46:39",
                  "url_fyyd": "https:\/\/fyyd.de\/episode\/1662345",
                  "description": "Freitag, 14. April 2017, 15:05 Uhr<p>Frankreich steht seit Monaten Kopf."
              },
              {
                  "title": "LdN051 BVB-Bus, Steuern, Syrien, US-Au\u00dfen-\u201cPolitik\u201d, Altmaier",
                  "id": 1661432,
                  "guid": "podlove-2017-04-14t07:57:05+00:00-5ee52bc0e03190f",
                  "url": "https:\/\/www.kuechenstud.io\/lagedernation\/2017\/04\/14\/ldn051-bvb-bus-steuern-syrien-us-aussen-politik-altmaier\/",
                  "enclosure": "https:\/\/www.kuechenstud.io\/lagedernation\/podlove\/file\/1795\/s\/feed\/c\/mp3\/LdN051.mp3",
                  "podcast_id": 44980,
                  "imgURL": "",
                  "pubdate": "2017-04-14 10:07:59",
                  "duration": 3945,
                  "favedDate": "2017-04-17 16:45:58",
                  "url_fyyd": "https:\/\/fyyd.de\/episode\/1661432",
                  "description": "<p>Liebe Lage-Gemeinde!<\/p>\n<p>P\u00fcnktlich zu Ostertagen die neue Lage."
              }
          ]
      }
    }


### [POST /curate/{curation_id}/{episode_id}]

### Description

Adds OR removes the episode identified by episode_id into the curation identified by curation_id. The curation must be owned by the user identified by the accesstoken. The status of the episode inside this curation toggles. This will most likely change in future revisions of this API or at least will be detailed by two additional request.

#### Parameters

- **curation_id (required, int)** the curation's id
- **episode_id (required, int)** the episode's id

#### Response

    {
      "status": 1,
      "msg": "ok",
      "meta": {
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
      "data": "added Seitenwechsel - Ihr k\u00f6nnt mich mal 22.01.2016 (PODCAST) to Testfeed"
    }
---



# Collections

This part is all about collections at fyyd. The content part of collections are podcasts.



### [GET /collection/{id}[/podcasts]]

### Description

Returns information about a single collection, given the collection's id. May append podcasts, not paged at the moment.

#### Parameters

- **id (required, int)** the collection's id

#### Response

    {
      "status": 1,
      "msg": "ok",
      "meta": {
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
      "data": {
          "title": "Netzpolitik",
          "id": 1,
          "description": "(Netz)politische Podcasts",
          "layoutImageURL": "https:\/\/img.fyyd.de\/collection\/layout\/1.jpg",
          "thumbImageURL": "https:\/\/img.fyyd.de\/collection\/thumbs\/1.png",
          "microImageURL": "https:\/\/img.fyyd.de\/collection\/micro\/1.png",
          "slug": "netzpolitik",
          "user_id": 1000,
          "url": "https:\/\/fyyd.de\/user\/eazy\/collection\/netzpolitik",
          "podcasts": [
              {
                  "title": "#heiseshow (Audio)",
                  "id": 5037,
                  "xmlURL": "https:\/\/www.heise.de\/heiseshow.rss",
                  "htmlURL": "http:\/\/www.heise.de\/heiseshow.rss",
                  "imgURL": "https:\/\/www.heise.de\/imgs\/02\/5\/1\/1\/7\/THUMB_heiseshow_quadrat-b3e99ad376d2732e.jpg",
                  "status": 304,
                  "slug": "heiseshow-audio",
                  "layoutImageURL": "https:\/\/img.fyyd.de\/pd\/layout\/5037.jpg",
                  "thumbImageURL": "https:\/\/img.fyyd.de\/pd\/thumbs\/5037.png",
                  "microImageURL": "https:\/\/img.fyyd.de\/pd\/micro\/5037.png",
                  "language": "de",
                  "lastpoll": "2017-04-17 05:20:40",
                  "generator": null,
                  "user_id": null,
                  "categories": "62,64,63,8,9",
                  "lastpub": "2017-04-13 02:00:00",
                  "rank": 1,
                  "url_fyyd": "https:\/\/fyyd.de\/podcast\/5037",
                  "description": "Immer donnerstags um 16 Uhr diskutieren wir in der #heiseshow mit G\u00e4sten \u00fcber aktuelle Ereignisse aus der Hightech-Welt und der Netzpolitik",
                  "subtitle": "Jede Woche Donnerstag live (Audio)"
              },
              {
                  "title": "Breitband - Medien und digitale Kultur (ganze Sendung) - Deutschlandradio Kultur",
                  "id": 503,
                  "xmlURL": "http:\/\/www.deutschlandradiokultur.de\/podcast-breitband-medien-und-digitale-kultur-ganze-sendung.1552.de.podcast.xml",
                  "htmlURL": "http:\/\/www.deutschlandradio.de\/weiterleitung-breitband-de.233.de.html",
                  "imgURL": "http:\/\/www.deutschlandradiokultur.de\/media\/files\/2\/258cfe6db750912b0bb36410d2fdf775v2.jpg",
                  "status": 390,
                  "slug": "breitband-medien-und-digitale-kultur-ganze-sendung-deutschlandradio-kultur",
                  "layoutImageURL": "https:\/\/img.fyyd.de\/pd\/layout\/503.jpg",
                  "thumbImageURL": "https:\/\/img.fyyd.de\/pd\/thumbs\/503.png",
                  "microImageURL": "https:\/\/img.fyyd.de\/pd\/micro\/503.png",
                  "language": "de",
                  "lastpoll": "2017-04-17 17:12:06",
                  "generator": null,
                  "user_id": null,
                  "categories": 62,
                  "lastpub": "2017-04-15 13:05:01",
                  "rank": 14,
                  "url_fyyd": "https:\/\/fyyd.de\/podcast\/503",
                  "description": "Feed provided by Deutschlandradio. Click to visit.",
                  "subtitle": "Die Beitr\u00e4ge zur Sendung"
              }
           ]
    	}
    }

### [POST /collect/{collection_id}/{podcast_id}]

### Description

Adds OR removes the podcast identified by podcast_id into the collection identified by collection_id. The collection must be owned by the user identified by the accesstoken. The status of the podcast inside this collection toggles. This will most likely change in future revisions of this API or at least will be detailed by two additional request.

#### Parameters

- **collection_id (required, int)** the collection's id

- **podcast_id (required, int)** the podcasts's id 


#### Response

    {
      "status": 1,
      "msg": "ok",
      "meta": {
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
      "data": "added (or removed?) Freak Show to Gamechanger"
    }
---



# Search

This request is the only one in this section for now. The search API will grow in the near future, drafts are already written on how to manage this important part of fyyd's API.

### [GET /search/episode]

### Description

This request tries to find an episode inside fyyd's database, matching any or some of a set of given criteria.

This reflects Skoon's need to find an episode's id to add to the user's curation. 

Since the parameters composition is too complex for a restful URL, you have to add queries. Remember to urlencode all strings or else you might break your requests.

#### Parameters

* **title (optional, string)** the episode's title. Search might use parts of the string to find the episode.
* **guid (optional, string)** the episodes GUID as stated inside the podcasts feed.
* **podcast_id (optional, int)** the podcast's id in fyyd's database.
* **podcast_title (optional, string)** the podcast's title. Search might use parts of the string to find the podcast.
* **pubdate (optional, string)** the pubDate as stated inside the podcasts feed.
* **duration (optional, int)**  the duration of the episode in seconds.
* **url (optional, string)** the episode's url as stated inside the podcast's feed.
* **term (optional,string)** a search term to find inside the episodes.

Please note: title, guid, pubdate, duration, url and term add episodes together. Think of an logical OR.

In contrast to that, podcast_id and podcast_title restrict all episodes to podcasts matching to one of podcast_id or podcast_title.

* **count (optional, int, default: 10)** 

#### Response

    {
      "status": 1,
      "msg": "ok",
      "meta": {
          "API_INFO": {
              "API_VERSION": 0.2
          }
      },
      "data": [
          {
              "title": "FS195 Dein Butler ist ein Zombie",
              "id": 1597636,
              "guid": "podlove-2017-03-22t23:23:57+00:00-f1bfca935c876bc",
              "url": "http:\/\/freakshow.fm\/fs195-dein-butler-ist-ein-zombie",
              "enclosure": "https:\/\/tracking.feedpress.it\/link\/13453\/5554460\/fs195-dein-butler-ist-ein-zombie.m4a",
              "podcast_id": 85,
              "imgURL": "",
              "pubdate": "2017-03-23 02:16:34",
              "duration": 14632,
              "url_fyyd": "https:\/\/fyyd.de\/episode\/1597636",
              "description": "\n<p>Open Source Development \u2014 Ultraschall \u2014 Podlove Publisher \u2014 Podcast Empanzipation \u2014 Thunderbolt..."
          }
      ]
    }
