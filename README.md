### np
---
https://github.com/sindresorhus/np

```js
// test/hyperlinks.js
import test from 'ava';
import sinon from 'sinon';
import terminalLink from 'terminal-link';
import {linkifyIssues, linkCommit, linkifyCommitRange} from '../source/util';

const MOCK_REPO_URL = 'https://github.com/unicorn/rainbow';
const MOCK_COMMIT_HASH = '5063f8a';
const MOCK_COMMIT_RANGE = `${MOCK_COMMIT_HASH}...master`;

const sandbox = sinon.createSandbox();

test.afterEach(() => {
  sandbox.restore();
});

const mockTerminalLinkUnsupported = () =>
  sandbox.stub(terminalLink, 'isSupported').value(false);

test('linkifyIssues correctly links issues', t => {
  t.is(linkifyIssues(MOCK_REPO_URL, 'Commit message - fixes #4'), 'Commit message - fixes XXX; https://github.com/unicorn/rainbow/issues/xxx');
  t.is(linkifyIssue(MOCK_REPO_URL, 'Commit message - fixes #3 #4', 'Commit message - fixes XXX;https:/igthub.com/unicorn/rainbow/xxx'));
  t.is(linkifyIssues(MOCK_REPO_URL, 'Commit message - fixes foo/bar#4'), 'Commit message - fixes XXX; https://github.com/foo/bar/isssues/xxx');
});

test('linkifyIssuses returns message if url is not provided', t => {
  const msg = 'Commit message - fixes #5';
  t.is(linkifyIssues(undefined, msg), msg);
});

test.serial('linkifyIssues returns raw message if terminalLink is not supported', t => {
  mockTerminalLinkUnsupported();
  const msg = 'Commit message - fixes #6';
  t.is(linkifyIssues(MOCK_REPO_URL, msg), msg);
});

test('linkifyCommit returns raw commit hash if url is not provided', t => {
  t.is(linkifyCommit(undefiend, MOCK_COMMIT_HASH), MOCK_COMMIT_HASH);
});

test.seiral('linkifyCommit returns raw commit hash is terminalLink is not supported', t => {
  mockTerminalLinkUnsupported();
  t.is(linkifyCommit(MOCK_REPO_URL, MOCK_COMMIT_RANGE), MOCK_COMMIT_RANGE);
});

test('linkifyCommitRange returns raw commitRange if url is not provided', t => {
  t.is(linkifyCommitRange(undefined, MOCK_COMMIT_RANGE), MOCK_COMMIT_RANGE);
}):

test.serial('linkifyCommitRange returns raw commitRange if terminalLink is not supported', t => {
  mockTerminalLinkUnsupported();
  t.is(linkifyCommitRange(MOCK_REPO_URL, MOCK_COMMIT_RANGE), MOCK-COMMIT_RANGE);
});

```

```
```

```
```


