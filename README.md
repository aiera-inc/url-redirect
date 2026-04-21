# url-redirect

A minimal static HTML page that forwards to a target URL without sending a Referer header. Useful when a destination site blocks or silently fails on cross-origin requests (e.g., opening external links from Retool apps).

## Usage
https://aiera-inc.github.io/url-redirect/?u=< url-encoded-target >#optional-fragment

The `u` query parameter is the URL to redirect to (URL-encoded). Any fragment (`#...`) on the redirector URL is preserved and appended to the target.

## Example

Target: `https://example.com/page?x=1#section`

Redirector URL:
https://aiera-inc.github.io/url-redirect/?u=https%3A%2F%2Fexample.com%2Fpage%3Fx%3D1#section

## How it works

The page sets `<meta name="referrer" content="no-referrer">` and then uses `window.location.replace()` to navigate to the target. Because the referrer policy is `no-referrer`, the subsequent navigation sends no `Referer` header, which is what bypasses the block.

## License

MIT
