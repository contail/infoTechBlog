+++
date = "2018-10-17T15:10:40+00:00"
title = "파이썬 - “SSL: CERTIFICATE_VERIFY_FAILED” 에러"

+++
파이썬에서 urllib 혹은request를 보낼 때 

간혹 이와 같은 오류를 접할 수 있다. 

이때 ssl인증을 거쳐갈 임시의 context를 생성 할 수 있다.

    import ssl
    ssl._create_default_https_context = ssl._create_unverified_context

  
위의 구문을 추가해주면 된다.

자세한 원인과 해결 방법은

*  [https://stackoverflow.com/questions/27835619/urllib-and-ssl-certificate-verify-failed-error](https://stackoverflow.com/questions/27835619/urllib-and-ssl-certificate-verify-failed-error "https://stackoverflow.com/questions/27835619/urllib-and-ssl-certificate-verify-failed-error")