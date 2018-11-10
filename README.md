## Deep Clone

> Deep cloning npm module which is used to deep clone(copy) multiple data structures.

[![npm](https://img.shields.io/badge/npm-v2.0.0-blue.svg)](https://www.npmjs.com/package/@shashikhanal/deep-clone)
[![Build Status](https://travis-ci.org/shashikhanal/deepClone.svg?branch=master)](https://travis-ci.org/shashikhanal/deepClone)
[![GitHub license](https://img.shields.io/github/license/shashikhanal/deepClone.svg)](https://github.com/shashikhanal/deepClone/blob/master/LICENSE)


## Usage
```js
// import the module
let deepClone = require('@shashikhanal/deep-clone');
const locations = ['HK', 'SG', 'UK', 'NZ', 'AU'];

const employeeDefaults = {
    name: 'undefined',
    reserved: undefined,
    info: {
        address: 'Nepal',
        level: 1,
        age: {
            DOB: 'YYY-MMM-DDD',
            today: new Date(1534235210553)
        }
    }
};

function Company() {
    Object.assign(this, employeeDefaults);
    this.company = 'Zegal';
    this.info.locations = locations;
}

Company.prototype.speakLocation = function(location) {
    const locations = {
        HK: 'Hong Kong',
        SG: 'Singapore',
        UK: 'England and Wales',
        NZ: 'New Zealand',
        AU: 'Australia'
    };

    return locations[location] || 'Hong Kong';
};

Company.prototype.getLocations = function() {
    let locations = [];

    if (this.info.locations) {
        this.info.locations.forEach(location => {
            locations.push(this.speakLocation(location));
        });
    }

    return locations;
};

const object1 = new Company();
console.log(deepClone(object1));
// { name: 'undefined',
//     reserved: undefined,
//     info:
//      { address: 'Nepal',
//        level: 1,
//        age: { DOB: 'YYY-MMM-DDD', today: 2018-08-14T08:26:50.553Z },
//        locations: [ 'HK', 'SG', 'UK', 'NZ', 'AU' ] },
//     company: 'Zegal',
//     speakLocation: [Function],
//     getLocations: [Function] }

const arr1 = [1, 2, 3];
console.log(deepClone(arr1));
// [ 1, 2, 3 ]

const obj1 = {
    name: 'Sample Object name !',
    arr1: [100, 200],
    num1: 200,
    und: undefined
};
console.log(deepClone(obj1));
// { name: 'Sample Object name !',
//     arr1: [ 100, 200 ],
//     num1: 200,
//     und: undefined }

```

## Contributing
``` bash
# clone the project 
git clone git@github.com:shashikhanal/deepClone.git

# change directory
cd deepClone

# install dependancies
npm install

# Make your changes and add a test for the new feature or bug found.
# and submit a pull request
git add -A && git commit -m "added a feature" && git push origin master
```
Finally, submit a pull request and grab a beer. Cheers!

## License

[MIT License](https://opensource.org/licenses/MIT)
