# android-sample-api-manager

# Overview

These code files are a general package for an Android device to receive an access token via Three-Legged OAuth.

# Getting Started

1. Add OauthRequestBody.java, ApiUtils.java, OAuthService.java, and OAuthResponse.java to your source folder.

2. Implement the following method “getData” wherever you need to authorize and collect and access token.

```

    public void getData(View v) {
        String authorization = "authorization_example";
        //String contentType = "contentType_example";
        String contentType = "application/json";
 
        Map<String, String> map = new HashMap<>();
        map.put("Authorization", authorization);
        map.put("Content-Type", contentType);
        final OAuthRequestBody requestBody = new OAuthRequestBody("grantType_example","scope_example");
 
        mService.makeOAuthCall(requestBody, map).enqueue(new Callback<OAuthResponse>() {
            @Override
            public void onResponse(Call<OAuthResponse> call, Response<OAuthResponse> response) {
	     //****** Below is the line to access the Response Body, and the Access_Token *******
                //OAuthResponse responseBody = response.body();
                Toast.makeText(activityContext, "Success", Toast.LENGTH_LONG).show();
            }
 
            @Override
            public void onFailure(Call<OAuthResponse> call, Throwable t) {
                Toast.makeText(activityContext, "Failure", Toast.LENGTH_LONG).show();
            }
        });
    }

```

3. Given a successful response, your access token will be in the the response.body(). (More details can be found in OAuthResponse.java). So uncomment the line specified above and you now have an access token!

# Acknowledgments

This code does not include a gradle or any of the other relevant Android project files. It is not a standalone sample app, but rather some supporting files to show you how to implement Three-legged-OAuth using the Citi APIs.
