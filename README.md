# Gracenote Metadata for Silo

Maintained by [ATTMonk](https://github.com/attmonk).

Planned Gracenote metadata provider for Silo, following the integration patterns of
the official TMDB and TVDB plugins.

**Status: parked pending expanded Gracenote API access.** This repository records
the scope and prerequisites; it does not contain an installable plugin yet.

## Identity

- Repository: `attmonk/attmonk-plugin-metadata-gracenote`
- Proposed plugin ID: `silo.attmonk.gracenote`
- Proposed provider ID: `gracenote`
- Planned language/runtime: Go with the published Silo plugin SDK

## Planned scope

- Movie and series search and matching, including title, year, and language.
- Descriptions, genres, release and air dates, runtime, content ratings, and credits
  where the licensed API supplies them.
- Seasons and episodes, with complete pagination.
- Posters, backdrops, logos, and episode stills where available and entitled.
- Gracenote identifiers retained in Silo provider IDs.
- Metadata provider priority alongside TMDB, TVDB, and other providers.
- Image resolver support for stable `gracenote://` artwork references.
- User-supplied credentials in plugin configuration; no bundled API key.

Use one plugin with an internal API adapter boundary. Start with OnConnect/TMS.
Keep enterprise On API support as a future adapter, pending its documentation,
credentials, and verified response samples. Supporting an API is separate from
the access granted to an individual account.

## Access checkpoint

The application registration is active, but Gracenote granted only the **Public
plan**. The registration email lists these available methods:

- New Shows Airing on TV
- Movies Airing on TV
- Sports Events Airing on TV
- Movies Playing in Local Theatres

These do not provide the general search, program details, and episode enumeration
needed for the planned library metadata provider.

Gracenote's published legacy FAQ describes a free, approved 30-day Sample plan
and contract-based R&D/production access. Current availability and ongoing
personal/noncommercial terms still need confirmation with Gracenote. The legacy
site says active documentation moved to its new developer portal in September
2026. No permanent free tier sufficient for the full plugin has been verified.

### Request for expanded access

Suggested message to Gracenote:

> I'm developing an open-source metadata provider plugin for Silo, a self-hosted
> media server. Could you approve Sample access to Program Search, Program
> Details, Series Details, and Series Episodes?
>
> I'd also like to evaluate Program Images and image delivery for posters,
> backdrops, and episode stills.
>
> Please confirm the evaluation period and whether you offer a free or low-cost
> option for ongoing personal, noncommercial use, with each plugin user supplying
> their own API key.

## Resume checklist

- Confirm expanded endpoint access and ongoing usage terms.
- Confirm image delivery access and the account's image host configuration.
- Obtain current API documentation and sanitized sample responses.
- Recheck the current official plugin interfaces and published SDK version.
- Implement and validate OnConnect search, metadata, episode pagination, and
  artwork mapping using fixtures, followed by live validation with approved access.
- Evaluate enterprise On API separately when its access is available.
- Add packaging, CI/release automation, and a catalog entry once ready to ship.

## References

- [Official Silo TMDB plugin](https://github.com/Silo-Server/silo-plugin-metadata-tmdb)
- [Official Silo TVDB plugin](https://github.com/Silo-Server/silo-plugin-metadata-tvdb)
- [Silo plugin SDK](https://github.com/Silo-Server/silo-plugin-sdk)
- [Gracenote access plans](https://developer.tmsapi.com/TMS_Data_Delivery_APIs)
- [Gracenote FAQ](https://developer.tmsapi.com/page/Frequently_Asked_Questions)
- [Gracenote API explorer](https://developer.tmsapi.com/io-docs)
- [Gracenote developer portal](https://devportal.gracenote.com/)
