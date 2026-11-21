<img src="assets/logo.png" width="112" height="112" alt="Blyx penguin placing a version tag between a filled and an open endpoint.">

# VersionBand

Check membership of a numeric-version core in a half-open dependency interval. This Blyx library is part of the packaging and code quality collection.

String sorting places 1.10 before 1.2. Check numeric ordering and the consumer's upper bound separately. [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-versionband.git
cd blyx-versionband
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-versionband) · [Package page](https://www.blyx-lang.space/packages/versionband) · [Handbook](https://doc.blyx-lang.space/guide/bowerbird)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-versionband.git vendor/versionband
```

```blyx
use vendor::versionband::versionband;

fn main() {
    let version = [1, 2, 0];
    let lower = [1, 2, 0];
    let upper = [2, 0, 0];
    let result = versionband_contains(version, lower, upper);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
1
0
0
```

## API

`versionband_contains(version, lower, upper)`

Returns [inside, below lower, at or above upper]. All versions have three integer components and lower must precede upper. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| version | Vector of values, each a nonnegative exact integer |
| lower | Vector of values, each a nonnegative exact integer |
| upper | Vector of values, each a nonnegative exact integer |

## In use

[Bowerbird](https://github.com/Rahulchaube1/blyx-bowerbird) uses this module to decide whether a proposed numeric-core dependency upgrade fits a declared version range.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-versionband/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). Read the [artwork notice](assets/NOTICE.txt) for credits.

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
