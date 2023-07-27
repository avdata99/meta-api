# Some Meta API test

Some notes about Meta api test.  

## Get an access token

```
CLIENT_ID=XX
CLIENT_SECRET=YY

curl -X GET "https://graph.facebook.com/oauth/access_token?client_id=$CLIENT_ID&client_secret=$CLIENT_SECRET&grant_type=client_credentials"
```

JSON Response.  

```
{"access_token":"your-client-id|some-token","token_type":"bearer"}
```

TOKEN=your-client-id|some-token

```
curl -G -d "search_terms='cordoba'" \
    -d "ad_type=POLITICAL_AND_ISSUE_ADS" \
    -d "ad_reached_countries=['AR']" \
    -d "access_token=$TOKEN" \
    "https://graph.facebook.com/v17.0/ads_archive"
```

If your facebook app is not ready, you will get an error like this:

```
{
    "error":{
        "message":"Application does not have permission for this action",
        "type":"OAuthException",
        "code":10,
        "error_subcode":2332004,
        "is_transient":false,
        "error_user_title":"App role required",
        "error_user_msg":
            "You need to be assigned a role by the app owner to continue.
            Learn more at
            https://developers.facebook.com/docs/development/build-and-test/app-roles",
        "fbtrace_id":"xxxx"
    }
}
```

To fix this you need to add the `ads_read` permission to your app.  



## Other links

More references:

 - List your facebook apps: https://developers.facebook.com/apps/
 - Test api online: https://developers.facebook.com/tools/explorer
 - Test specific endpoint, `ads_archive`: https://developers.facebook.com/tools/explorer/?method=GET&path=ads_archive%3Fad_reached_countries%3DAR&version=v17.0
