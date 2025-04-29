# Data Mining & Information Retrieval Deadlines Countdown

Based on [ai-deadlines](https://aideadlin.es) by @abshkdz, [sec-deadlines](https://sec-deadlines.github.io), and [se-deadlines](https://se-deadlines.github.io)

## Adding/updating a conference

* Update `_data/conferences.yml`. You can do that on Github or locally after forking the repo.
* Send a pull request

### Conference entry record
Example record:

```
- name: CIKM
  description: ACM Conference on Information and Knowledge Management - Full & Applied Research Papers
  year: 2025
  link: https://cikm2025.org
  deadline: 
  - "2025-05-23 23:59"
  date: November 11 - November 14, 2025
  place: Seoul, South Korea
  note: Mandatory abstract deadline on May 16 2025.
  tags: [CO, FPT, APT]
```

Descriptions of the fields:

| Field name    | Description                                                             |
|---------------|-------------------------------------------------------------------------|
| `name`\*      | Short entry name, without year                 |
| `description` | Description, or long name                      |
| `year`\*      | Year the event is happening                    |
| `link`\*      | URL to the entry home page                     |
| `deadline`\*  | A list of deadlines.                           |
| `date`        | When the entry is happening                    |
| `place`       | Where the entry is happening                   |
| `note`        | Extra notes about the deadline                 |
| `tags`        | One or multiple tags                           |

Fields marked with asterisk (\*) are required.

### Deadline format

The *deadline* field can contain:

1. The simplest option: a date and time in ISO format. Example: `["2017-08-19 23:59"]` (Note that you need to wrap even a single deadline in a list).
2. If a deadline is rolling, you can use a template date, just substitute the
   year with `%y` and the year before the conference with `%Y`. Example:
   `["%y-01-15 23:59"]` means there is a deadline on the 15th January in the
   same year as the conference.
3. A list of (1) or (2). Example of two rolling deadlines, with one in the end
   of October in the year prior to the conference year, and the second in the
   end of February in the same year as the conference:
  ```
  - "%Y-10-31 23:59"
  - "%y-02-28 23:59"
  ```
4. If the deadline has not yet been announced, use `["TBA"]` as the deadline for the conference (case sensitive.) It will show up at the bottom of future conferences.

On the page, all deadlines are displayed in viewer's local time (that's a feature).

*Note:* If the deadline hour is `{h}:00`, it will be automatically translated into `{h-1}:59:59` to avoid pain and confusion when it happens to be midnight in local time.


### Timezones

Please remember that the timezone should be AoE (Anywhere on Earth) when you submit a pull request.


### Note

The *note* field can be used to indicate additional information about a deadline. For example, if an abstract is required before the deadline.

### Tags

The *tag* field indicates the type of deadline entry you are adding. Users can filter deadlines based on tags. There are two main categories:

- **Venue type:** The type of venues the deadline indicates. For example, is it a conference (`CO`), a workshop (`WO`), or a special edition of a journal (`JO`).
- **Tracks:** Data Mnining conferences generally have multiple tracks with different goals, scopes, requirements, and deadlines. For example, CIKM 2025 has a Full Research Paper and an Applied Research Paper tracks. The former is a full research paper track (`FPT`), while the latter is an applied research track (`APT`). We are currently testing our tag groups for tracks and welcome any suggestions! :)

A complete tag list is available in [`types.yml`](_data/types.yml)