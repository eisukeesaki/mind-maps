# OAuth 

```text

OAuth
    solution
        How to provide for third party applications, delegated_access to protected resources without putting end-user's data at risk?
                                └─ allowing applications to talk to each other on behalf of end-user
    OAuth for user authentication
        point of view of this mind map
            developer of client
        actors
            protected resource
                owned by resource owner
                stored on OAuth provider's database
                accessed by client
                    upon successful access delegation process
                        to use it in services that the client provide to the resource owner
            resource owner
                owns protected resource
                    hosted on resource server
                        owned by OAuth provider
                consents to delegated access to protected resource
                                        └─ by client
            provider
                entity that provides OAuth
                    authorization server
                    resource server
            access token
                contains
                    token
                        right to perform operation
                    scope
                    user identifier
                    ttl
                    ...
                generated by authorization server
                    upon resource owner's consent
                    sent to client
                        as query string
                        sent to resource server by client
                            within request to access protected resource
                used by
                    client
                        as a means 
                            to access protected resource
                                on behalf of resource owner
                    resource server
                        as a means
                            to allow client to access protected resource
                                on behalf of resource owner
            validation code
                indicates validity of consent
                    unique for every generated consent form
                    inserted in consent form and sent to resource owner
                    sent back to authorization server by resource owner
            client
                of OAuth provider
                wants to
                    access resource server
                        perform actions on resource
                            on behalf of resource owner
        flow
            terminologies
                user = end-user
                app = app that developer is building which uses OAuth to authenticate its users into the system.
                provider = OAuth provider
            1. user attempts to login to app
            2. app redirect user to validation API of OAuth provider
            3. OAuth provider validates user
            4. OAuth provider redirects user back to app with an access token
            5. app makes a request to OAuth provider's identity server along with the access token in order to obtain user's information
            6. app creates session for the user using the obtained user information
    OAuth 2.0
        Google
            "Sign in with Google"
                required configurations on Google Cloud Console
                    ordered steps as of 2022-06-20
                        visit Google API Console
                            create or select existing project
                            configure consent screen
                                provide information
                                    application information
                                    application domain
                                        authorized domains
                                    developer contact information
                                configure scopes
                                    .../auth/userinfo.profile
                                    .../auth/userinfo.email
                                register test users
                            create credentials
                                OAuth client ID
                                    provide information
                                        authorized redirect URIs
                                    get client secret
                            ?verify application in order to allow all users on the internet to use OAuth 
                                https://support.google.com/cloud/answer/10311615?authuser=1#user-type
                request - response flow
                    browser makes GET request to my app's authentication route
                        > GET /authentication/federated/google HTTP/1.1
                        > Host: localhost:4242
                        > User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36
                    my app redirects browser to Google's authorization server
                        < HTTP/1.1 302 Found
                        < Location: https://accounts.google.com/o/oauth2/v2/auth
                            ?response_type=code
                            &redirect_uri=http%3A%2F%2F127.0.0.1%3A4242%2Foauth2%2Fredirect%2Fgoogle
                            &scope=profile%20email
                            &client_id=375386997323-qruca2jpo61batte6ohn288rk9m91432.apps.googleusercontent.com
                    browser makes GET request to Google's authorization server
                        > :authority: accounts.google.com
                        > :method: GET
                        > :path: /o/oauth2/v2/auth
                            ?response_type=code
                            &redirect_uri=http%3A%2F%2F127.0.0.1%3A4242%2Foauth2%2Fredirect%2Fgoogle
                            &scope=profile%20email
                            &client_id=375386997323-qruca2jpo61batte6ohn288rk9m91432.apps.googleusercontent.com
                        > cookie: SMSV=ADHTe-BUr-DS3RGDQLuumL0fckyhWcbalz1qlE2laluwBUzBAKHzAGh409ZfuWYu8sJ1KPtFOdm9JuFazzQtQr5nx0rAqmmqL5iTqZn0oNNa2M3EkESeEmc; user_id=101817407341620423232; LSOLH=AH+1Ng32PR8Xhf2h4NrZxuH6Z2BETcwCldfiAuFL6fiQAwiI/C2E2kINGVmcns2kafbsrOBAtetK; ACCOUNT_CHOOSER=AFx_qI6RwO5I5nYvW8uNjQEo3OZYeJlAJufne71L4Lom9JK_rBMaqnFQZaNSr-XNPxzd_uqT-AC0YCbZog6mbvMD9ekLlxSFUCjrzyT63jaEG2L8mp6UBwqEtGTf_zeDt6_DCipkwI2u; __Host-GAPS=1:hJG_pc27CcZEu0O9Vv-m5Y40PjeZNCd7RA_53Kyaq9dN6yVkNz50E9dzHrkVQz0V4_-bHI4flw4tUUPyCDgOmHEImFTTkw:JzxPkZPgNwniga0r
                        > user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36
                    Google's authorization server responds with a sign in form
                        < set-cookie: ...
                        < strict-transport-security: max-age=31536000; includeSubDomains
                        query string parameters
                            response_type: code
                            redirect_uri: http://127.0.0.1:4242/oauth2/redirect/google
                            scope: profile email
                            client_id: 375386997323-qruca2jpo61batte6ohn288rk9m91432.apps.googleusercontent.com
                        response body
                            <!doctype html>
                            <title>Sign in - Google Accounts</title>
                    browser sends sign in form
                        ?
                    browser makes GET request to ?
                        > :authority: accounts.google.com
                        > :method: GET
                        > :path: /signin/oauth/consent
                            ?authuser=0
                            &part=AJi8hAM7BT9mk6cIWB5omW0r10w8e4_CtJZLvQQE_4cqppg6367m5lfSc2RkOYVY2ptsdEawZpe-7Q8eO_46R9khCRm_UeOy06o5WzuV15mYPhLM1_5WEwYJtOhG3wDTcWkfoHMuYLVqc2VbVp57bJn-SaZUw-Nnx-gnPVnZcXVod97XWj7GPCNgwQdln6FiRUGvkUVe-5DoIR0U_7YqwDarDhRK2q8ql_qK-3A4Fn0VFW_tBTcOYzmnTFc28L8EbR1HvQbcJXkEUs9cUSedO3LfzJSYz9m9kdhQFBLADjEHFFcFZW2AbZ58ngb6QbKWIW0FSXaYGu1AMU__mFY3TjgN9pKGx9JXhZSR4IRremYCNrySkwCLE1Vxw0wKL-pEoaRhqZZxTl7-uYL3JCTD15awY4pqy0ZoBQGlz8jFUFfpsNxuin1rHuAhJFPzkDxprIKpEIL7UPfRlWGfPvdnM4K9nzbKaYEEkg
                            &as=S1393328610%3A1658953194001428
                            &client_id=375386997323-qruca2jpo61batte6ohn288rk9m91432.apps.googleusercontent.com
                            &rapt=AEjHL4NISk_DPvUlRC0h7FZBTPvP9Mme5SRRStX0fVztC0BS--jyiR3ife1nf_BFxufg7A5llk30-pghRRZh71j_pezJyFvCgA
                        > cookie: SMSV=ADHTe-BUr-DS3RGDQLuumL0fckyhWcbalz1qlE2laluwBUzBAKHzAGh409ZfuWYu8sJ1KPtFOdm9JuFazzQtQr5nx0rAqmmqL5iTqZn0oNNa2M3EkESeEmc; user_id=101817407341620423232; LSOLH=AH+1Ng32PR8Xhf2h4NrZxuH6Z2BETcwCldfiAuFL6fiQAwiI/C2E2kINGVmcns2kafbsrOBAtetK; SID=Mggw0qE_SgnKqilUuqhryaxDHL710-Whcij3yVXSG0aHbwTi7TWW9og3e9PADRSr6F6aow.; __Secure-1PSID=Mggw0qE_SgnKqilUuqhryaxDHL710-Whcij3yVXSG0aHbwTimaCPVA_k0J0Qg1KfogtnIQ.; __Secure-3PSID=Mggw0qE_SgnKqilUuqhryaxDHL710-Whcij3yVXSG0aHbwTiXBwhA9UU6Co1TInftaMk1w.; HSID=A2kaKStb80E9gNkcC; SSID=AqweinpB7Rs0DjFZU; APISID=9fi8eFROPQ8aOz-l/AGjaCqRzRXpwzMFOO; SAPISID=Oh5wp7N9VQMJGEhc/A9KuJVN6LVbauJwqX; __Secure-1PAPISID=Oh5wp7N9VQMJGEhc/A9KuJVN6LVbauJwqX; __Secure-3PAPISID=Oh5wp7N9VQMJGEhc/A9KuJVN6LVbauJwqX; __Host-GAPS=1:4xAS_rc33BbFVuq2j2UhwAklHuauJqh6GPzMfJWDiSHdpMC3EtKEsu1gvuYG1Z7v5U-BjzhSYN012Psr8adMSfdZlUM6Mg:COYDvieXUlOvRZdN; NID=511=MR9fJ4wnm0UWYOwSSU05Np_YNVHYKwEMNgmTHCKUwrQUm9ZvqACea7hOBlzdmh1L4d8456BS1Nw5ArK4Nop1LJAQ8qkk2cnHn6a1a48ToL65aorUfhkP3T0Fwh23FLdHYKFy_UAFptA8l4e7gLZbuNrtusfUUAMpFWdBlfXcx6Y6wFxevybGGFmQBvv1; LSID=s.CA|s.DE|s.youtube:Mggw0umKszM80bQkzrAW2LhSN0nnZkam5mLxqEhxa--zpq0kvsBiEVXolkh99-pytBzCbg.; __Host-1PLSID=s.CA|s.DE|s.youtube:Mggw0umKszM80bQkzrAW2LhSN0nnZkam5mLxqEhxa--zpq0kbiM-869fpLf5g7MMAjAOIA.; __Host-3PLSID=s.CA|s.DE|s.youtube:Mggw0umKszM80bQkzrAW2LhSN0nnZkam5mLxqEhxa--zpq0k42onw9BGdxbTFVxtc_ePjQ.; ACCOUNT_CHOOSER=AFx_qI5_7Wd6vgr638cbvkEnc3jo_-JFoSvmg3mnJiUBje00qoaAVgVzu7S3S_22t7_TkXnM4qwKMAQuzJT6Z68K8pxMzPjc82eGpWRmBiN7NVwDmd_B7F9rimE7kykIP60Vayo2VGgo; SIDCC=AJi4QfHvrFQ_LF0B5uu6z-YRG_BzXfJ7Ive3vM3jeSGgLhyBzJ9lLdI0u047P4XAVT3O3r_I; __Secure-1PSIDCC=AJi4QfFlBE-dTRKIxLhlcsZsaSTls72I59UfT3Jmc5aLRSmKYFXiscH0dr5sEwMXNy4o97Pj; __Secure-3PSIDCC=AJi4QfHmQZM-yUjFUQgGPciB6Bx0sub9ybYhlUfjMztU_sFuyWl9GgQCXB7NXlPa0HNZipiB
                        > user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36
                   Google's authorization server redirects browser to my app's redirect endpoint
                       < location: http://127.0.0.1:4242/oauth2/redirect/google(, which fetches tries to fetch the user's Google profile)
                           ?code=4%2F0AdQt8qgps219VUdCnjn4vprN4CxRcW0ghc-dYB2dyEsLCIF4DEJH9uiA0zAhH2OA5zXEWg
                           &scope=email+profile+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.profile+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.email+openid
                           &authuser=0
                           &prompt=consent
                       < set-cookie: ...
                       < set-cookie: ...
                       < set-cookie: ...
                       < set-cookie: ...
                       query string parameters
                           authuser: 0
                           part: AJi8hAM7BT9mk6cIWB5omW0r10w8e4_CtJZLvQQE_4cqppg6367m5lfSc2RkOYVY2ptsdEawZpe-7Q8eO_46R9khCRm_UeOy06o5WzuV15mYPhLM1_5WEwYJtOhG3wDTcWkfoHMuYLVqc2VbVp57bJn-SaZUw-Nnx-gnPVnZcXVod97XWj7GPCNgwQdln6FiRUGvkUVe-5DoIR0U_7YqwDarDhRK2q8ql_qK-3A4Fn0VFW_tBTcOYzmnTFc28L8EbR1HvQbcJXkEUs9cUSedO3LfzJSYz9m9kdhQFBLADjEHFFcFZW2AbZ58ngb6QbKWIW0FSXaYGu1AMU__mFY3TjgN9pKGx9JXhZSR4IRremYCNrySkwCLE1Vxw0wKL-pEoaRhqZZxTl7-uYL3JCTD15awY4pqy0ZoBQGlz8jFUFfpsNxuin1rHuAhJFPzkDxprIKpEIL7UPfRlWGfPvdnM4K9nzbKaYEEkg
                           as: S1393328610:1658953194001428
                           client_id: 375386997323-qruca2jpo61batte6ohn288rk9m91432.apps.googleusercontent.com
                           rapt: AEjHL4NISk_DPvUlRC0h7FZBTPvP9Mme5SRRStX0fVztC0BS--jyiR3ife1nf_BFxufg7A5llk30-pghRRZh71j_pezJyFvCgA
                    browser makes GET request to my app's redirect URL(, which fetches tries to fetch the user's Google profile)
                        >  GET /oauth2/redirect/google?code=4%2F0AdQt8qgps219VUdCnjn4vprN4CxRcW0ghc-dYB2dyEsLCIF4DEJH9uiA0zAhH2OA5zXEWg&scope=email+profile+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.profile+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.email+openid&authuser=0&prompt=consent HTTP/1.1
                        >  Cookie: session-id=s%3ARDtBNs9ffdRrjXpKAb1eDng8ChghtBmj.G9gLNyL8F4DHe5bUr2qNhEJmwjcC9Rk6rfuL14rp1tM
                        >  Host: 127.0.0.1:4242
                        >  User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36
                    Google's authorization server redirects browser to one of my app's endpoints which was predetermined by me
                        <  HTTP/1.1 302 Found
                        <  Location: /maplist
                        <  Content-Type: text/html; charset=utf-8
                        <  Content-Length: 60
                        <  Set-Cookie: session-id=... Path=/; HttpOnly
                        query string parameters
                            code: 4/0AdQt8qgps219VUdCnjn4vprN4CxRcW0ghc-dYB2dyEsLCIF4DEJH9uiA0zAhH2OA5zXEWg
                            scope: email profile https://www.googleapis.com/auth/userinfo.profile https://www.googleapis.com/auth/userinfo.email openid
                            authuser: 0
                            prompt: consent
            identity server
                https://accounts.google.com
                    authentication
                        GET /login/federated
                        logged in
                            obtains consent from user
                                release identity to third party

```

