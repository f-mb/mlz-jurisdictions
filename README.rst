======================
MLZ Jurisdictions List
======================

This is a list of `URN:LEX`__ jurisdiction codes, as used in
`Multilingual Zotero`__ (MLZ) and the `MLZ extended CSL schema`__
for the formatting of citations.

__ https://datatracker.ietf.org/doc/draft-spinosa-urn-lex/
__ https://github.com/fbennett/zotero/tree/multi
__ https://github.com/fbennett/schema

The content here is a single JSON object. The top-level keys
of the object are single country or institution codes. Country
codes are drawn from `ISO-3166`__, per the URL:LEX proposal
document. Institution codes are set as domain names, as
permitted by URN:LEX. The specific domain names chosen are
arbitrary, and may differ from the choices made by other
projects. [#]_ 

__ http://www.iso.org/iso/country_codes.htm

Each key maps to a child object containing one mandatory and one
optional key. The mandatory ``name`` key provides a name for the
jurisdiction specified, suitable for use in generating menus and the
like. The optional ``children`` key maps to an object with URN:LEX
keys. The hierarchy does not currently recurse further: keys under a
``children`` key map to objects carrying only a ``name`` value.

At recursion boundaries, one of two arbitrary extensions is applied to
the top-level key, to provide an anchor for nesting distinct from the
country or institution name proper: ``subunit`` or ``federal``. The
``subunit`` extension is used to anchor subjurisdictions that have
authority independent of their container.  Thus, ``us;ca`` (the state
of California) is located beneath a top-level anchor ``us;subunit``.

The ``federal`` extension is used to anchor subsidiary hierarchies
that are dependent on their parent. Thus, ``us;federal;de`` (the
Federal District of Delaware) is located under the ``us;federal``
anchor.

The ``subunit`` and ``federal`` anchors have no meaning within the
URN:LEX scheme and should not be used for tagging content. The
URN:LEX keys and top level and below should be treated as a single
namespace, with no conflicts when the hierarchy is flattened to
a list of keys.

Others are welcome to use this schema in other projects. I would only
ask that, unless you abandon the scheme of organization entirely, you
push amendments back into the source here via a GitHub pull request.
It's not written anywhere that this needs to be the master mapping,
but it will save time all around if we treat this as our watering
hole for the present.

Enjoy!

Frank Bennett, Nagoya


.. [#] I'm not particularly happy with this situation, so if you know
       of a central repository of these things that offers standard
       codes for international organizations, by all means put a note
       and pointer in the project tracker.
