Handling token events
This library will automatically obtain an access_token, and automatically refresh the access_token if a refresh_token is present. The refresh_token is only returned on the first authorization, so if you want to make sure you store it safely. An easy way to make sure you always store the most recent tokens is to use the tokens event:

const client = await auth.getClient();

client.on('tokens', (tokens) => {
  if (tokens.refresh_token) {
    // store the refresh_token in my database!
    console.log(tokens.refresh_token);
  }
  console.log(tokens.access_token);
});

const url = `https://dns.googleapis.com/dns/v1/projects/${projectId}`;
const res = await client.request({ url });
// The `tokens` event would now be raised if this was the first request



Also consider http://www.passportjs.org/docs/google/

Insert this into the search code:
logger.info('JCA TOKEN: ' + authToken);
