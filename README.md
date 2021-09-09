var isGithubUrl = require('is-github-url');

// Valid examples
isGithubUrl('https://github.com/facebook');
 // => true
isGithubUrl('https://github.com/facebook/react');
 // => true
isGithubUrl('https://github.com/facebook/react/releases/tag/v0.14.0');
// => true
isGithubUrl('git@github.com:facebook/react.git');
// => true
isGithubUrl('git://github.com/facebook/react.git#gh-pages');
// => true

// Invalid examples
isGithubUrl('https://google.com');
 // => false
isGithubUrl('unknown://github.com');
// => false
isGithubUrl('http://facebook.github.io/');
// => false

// Repository mode can be used to check whether a passed URL
// is a valid repository URL
isGithubUrl('https://github.com/facebook/react', { repository: true });
// => true
isGithubUrl('https://github.com/facebook', { repository: true });
// => false
isGithubUrl('https://github.com/facebook/react/releases/tag/v0.14.0', {
  repository: true
});
// => false

// Strict mode is used to validate URLs before cloning
// Strict mode turns on automatically if URL contains git protocol
isGithubUrl('https://github.com/facebook/react.git', { strict: true });
// => true
isGithubUrl('https://github.com/facebook/react', { strict: true });
// => false
