# Distributed Hash Referencing Concept

Every static piece of data can be stored in a distributed file network and referenced by it's hash value or by hash value of an archive that contains this data.

Hashes of archives can be saved in a blockchain transaction in plain or encrypted form.

Encrypted hashes can be stored in a custom tag of TD12 (https://github.com/LumaRay/Blockchain-HRI) in a blockchain transaction. This way only valid application users will be able to decrypt and find corresponding files in P2P networks. 

Files in P2P networks can also be referenced by file names - e.g. blockchain transaction can contain several specific bytes of data that need to be hashed with a salt - and the result of this can be used for file name search in P2P networks (however in this case a valid file hash still needs to be stored in some way within the blockchain transaction in order to verify the file).

Store everything in a single zip or arc (zip - if uncompressed, arc - if lightest compression) with a name containing base58(sha2-256(of the zip/arc)). Or in any other convenient archive type like tar.gz, etc.

Use additional extensions to give the file more details: add it's type, index, date and other attributes like: 2018-11-22.58933.fund-transfer-execution.<hash>.zip

Check everything before zipping.

After you zip/arc data, calculate it's hash (sha256) and timestamp-sign this hash using online services, then put the in/out timestamp files alongside with the zip/arc and give them the same names as the zip/arc and zip/arc that all again.

Make zips with no compression whenever appropriate (e.g. when packing several zips/arcs).

Make arcs with lightest compression (-m1 -s8m) whenever appropriate (e.g. when packing text/compressible data and space is critical).

Form zips/arc of specific named parts / additional extensions, like:
    date-2018-11-07.level-<nLevel>.SHA2-256-<hash>.zip

Every part should start with attribute name with a dash ("date-", "SHA2-256-", and any other custom attribute like "level-", ...) followed by the attribute value of chars subset [A-Z,a-z,0-9,_].

Attributes are separated with a point symbol "."

Attributes should be ordered by names alphabetically: latin symbols (uppercase - lowercase) - numbers

Add a short digest to a filename that can verify the file name against the file's magnet/torrent hash link.

Zip/Arc can be converted to base58 strings, then added a prefix, e.g. $fileinfoblock-zip-v10-<data> for zipped info block of structure version 1.0 or $fileinfoblock-arc-v21-<data> for arc'ed info block of structure version 2.1

Include any type of document (txt/doc/pdf/...) containing e.g. agreement between parties, where you can place hashes of related documents packages.

Make a photo of a printed and signed document, save is as jpeg/png, pack, timestamp and pack again, encrypt archive if appropriate, then calculate hash and refer to this hash from another document.

Store all secret document files in a secure place and only publish their hashes.
