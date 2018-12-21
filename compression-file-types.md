# compression-file-types.md


Yes, what you did was one of the correct ways. To un-gzip a `.gz` file, use `gunzip` or `gzip -d`.

If your gzipped file is file.bin.gz, you can decompress it with:

`gunzip file.bin.gz`
This decompresses it to file.bin. If the operation succeeds, **the original file.bin.gz is automatically removed. This is to say that the gzipped file is replaced with the decompressed file.**

If you want to keep the original, pass the `-k/--keep` flag:

`gunzip -k file.bin.gz`
gzip behaves like gunzip when it is invoked with the -d/--decompress/--uncompress flag. So this works too:

`gzip -d file.bin.gz`
As with `gunzip`, the default behavior of `gzip -d` is to replace its input file once it succeeds. You can pass both `-d` and `-k` if you want to keep the input file.

(All of this applies regardless of what kind of file you want to decompress; none of it is specific to the file having .bin in its name--that's just part of the example I've used, to better match your situation.)

You can run man gunzip for more information, or gunzip --help for a summary of options.
[src](https://askubuntu.com/questions/946006/how-to-uncompress-a-bin-gz-file/946013#946013)
