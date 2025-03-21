# ifo-security-files

## Response headers server name and X-powered by should not show (Next.js)

### Steps

1. Open `next.config.js` file
2. Add the following code:

```javascript
module.exports = {
  async headers() {
    return [
      {
        source: "/(.*)", // Apply to all routes
        headers: [
          { key: "X-Powered-By", value: "" }, // Remove X-Powered-By
          { key: "serverName", value: "" }, // Remove or modify serverName
        ],
      },
    ];
  },
};
```

3. Remove the .next folder and re-run the build

After these steps, both tags will be empty
