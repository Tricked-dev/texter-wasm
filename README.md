# WasmCord - built plugins with rust

## Installing

install [WasmCord](https://github.com/Tricked-dev/WasmCord),
go to the wasmcord folder then into the wasmcord plugins folder ( if this doesn't exist restart discord ) then run `git clone -b dist https://github.com/Tricked-dev/texter-wasm`

## Getting started

Requirements [Rust](https://www.rust-lang.org/tools/install), [Wasmpack](https://rustwasm.github.io/wasm-pack/installer/), [NodeJs](https://nodejs.org/en/download/), Linux (someone please make a pr to add windows support) and [yarn](https://classic.yarnpkg.com/lang/en/docs/install/#debian-stable) (Optional)

1. run `make` to build the project
2. move the files inside the WasmCord/plugins/<yourplugin>/ folder
3. test the plugin out

## Creating a Command

First add the command data to the plugin() functions.

```rs
#[wasm_bindgen]
pub fn plugin() -> String {
    let mock = Plugin {
        command: "cool".to_owned(),
        description: "Mock people".to_owned(),
        usage: "{c} [people to mock]".to_owned(),
    };
    serde_json::to_string(&vec![mock]).unwrap()
}
```

Then make a function that has the name of the command,

```rs
#[wasm_bindgen]
pub fn cool() -> String {
    let response = Response {
        send: true,
        result: "This is a response".to_owned(),
    };
    serde_json::to_string(&response).unwrap()
}
```

Build the project

```sh
$ make build
```

Move the files and your first wasm powered plugin is done
