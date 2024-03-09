# See Commit Signature

Just learned[^1] you can see a commit's signature if it has any.

## Signed commit

https://github.com/lydavid/til/commit/6d4a96dc3bb6dfa3b7f73ce0b4034d49765d3ddc
```
git cat-file -p 6d4a96dc3bb6dfa3b7f73ce0b4034d49765d3ddc
```

```
tree 8d1138d4ac70535dde804f4c6d670e9a177661d6
parent e8affa9f0487457f7c46659acfd205c864f40199
author David Ly <22302001+lydavid@users.noreply.github.com> 1709517920 -0500
committer David Ly <22302001+lydavid@users.noreply.github.com> 1709517920 -0500
gpgsig -----BEGIN PGP SIGNATURE-----
 
 iQGzBAABCgAdFiEErL9Mp41XJvsZAwK+PpHZ9I7OeBQFAmXlLGAACgkQPpHZ9I7O
 eBTr4Av9Hztu3jwce8qdrwBQnwn7VRJxkSOW75j/oJVU5aYr31Yau9mqm29P49nt
 57MJdsn2GjHlgdgjcbtJoW1CTKXGBXiCHcqyhLA2Q3D/lOzfFsIxG8VzeBW2ovFq
 o+ZmVGiNVHnKB39E6XIN6rjidPSZs4sYbsFW1eVN/zcUQeMKeyNauL6DX51v5mYz
 ROrz6xuOnfncJNSVtx5CBBBUKaAECsCdzdbtx1cf3kSB9DgKxctRYF/3JH3fqviM
 5emphKUzeMtFPTi3OrYokUlq7Lvy/tMZfyU8UURDeKB4709L28hUrh6Edwlvk3Br
 LE0oN21GTwaj7g3NF7JmX6r3+dv585F8qradBQi9YAgR/HL+zLZXUtuNSg2qYCHa
 aOkgN9FVnIqD+Lvqr7sDQpq5MLEMnstr5GMjKGdP7KWVolIBqjdxB2wKnYjJO8QI
 z2rLRey8uPvtLlbhJv27g6fhoRazE8yeTZ/cQDWIMtmweZAwZ/g/YJK/0zU32As9
 gjj0NpNJ
 =jzFn
 -----END PGP SIGNATURE-----

sign commit
```

## Unsigned commit
https://github.com/lydavid/til/commit/e8affa9f0487457f7c46659acfd205c864f40199
```
git cat-file -p e8affa9f0487457f7c46659acfd205c864f40199
```

```
tree 6aab8c7bd589586395078956ae9141ffe46d3677
parent 61a26ad419eb893b963e93b15c665a739858e76d
author David Ly <22302001+lydavid@users.noreply.github.com> 1709503145 -0500
committer David Ly <22302001+lydavid@users.noreply.github.com> 1709503145 -0500

commit from phone
```

[^1]: https://youtu.be/aolI_Rz0ZqY?t=1248