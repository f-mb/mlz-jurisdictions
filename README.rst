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

Each key maps to a child object containing one mandatory key ``name``
to a string value, and optional keys ``federal`` and ``subunit``. When
either or both of these optional keys are present, they must be
accompanied by a sibling ``nickname`` key to a string value.

The ``federal`` and ``subunit`` keys each map to an object with
keys ``children`` and ``name``. The ``name`` key is a string
label describing the children (typically an empty string or
"federal"). A ``children`` key maps to an object containing
jurisdiction keys, each mapping in turn to an object with a ``name``
key to a string value, as at the top level of the overall object.

Jurisdiction keys must be unique across the entire object. Child
descriptions can be generated from the ``name`` and ``nickname`` values
with addressing something like this::

   parent = obj[key]["nickname"]
   name = obj[key]["federal"]["children"][subkey]["name"]
   type = obj[key]["federal"]["name"]
   "%s, %s (%s)" % (name,parent,type)

(Deployed code obviously needs to recurse across the object, so the
actual code will look rather different.)

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

=====

.. raw:: html

    <p xmlns:dct="http://purl.org/dc/terms/" xmlns:vcard="http://www.w3.org/2001/vcard-rdf/3.0#">
      <a rel="license"
         href="http://creativecommons.org/publicdomain/zero/1.0/">
        <img src="http://i.creativecommons.org/p/zero/1.0/88x31.png" style="border-style: none;" alt="CC0" />
      </a>
      <br />
      To the extent possible under law,
      <a rel="dct:publisher"
         href="https://github.com/fbennett/mlz-jurisdictions">
        <span property="dct:title">Frank Bennett</span></a>
      has waived all copyright and related or neighboring rights to
      <span property="dct:title">MLZ Jurisdictions List</span>.
    This work is published from:
    <span property="vcard:Country" datatype="dct:ISO3166"
          content="JP" about="https://github.com/fbennett/mlz-jurisdictions">
      Japan</span>.
    </p>




