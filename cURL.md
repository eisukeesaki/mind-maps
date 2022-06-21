# cURL

```text

curl
    set Cookie request header
        --cookie
        example
            curl -v --cookie "USER_TOKEN=Yes" http://127.0.0.1:5000/
    POST JSON
        set request header
            set representation header
                indicate type of resource in payload
                    Content-Type = MIME type = media type
                        --header
                            "Content-Type: application/json"
                        -d
                            shorthand for data
                            implies POST request unlike --data
                        example
                            curl -v \
                                --header "Content-Type: application/json" \
                                -d '{"email": "asuka@nerv.jp", "password": "letasukain"}' \
                                http://localhost:4242/api/v0/sessions

```

