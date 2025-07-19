---
title: "Oracle Free Tier VM 설정 가이드"
date: 2025-07-19
categories: [Community, Server] # 대분류 (사이드바에 표시됨)
tags: [Oracle, OracleVM, VM, Virtual machine, Setting, Free Tier, Oracle Free Tier]     # 소분류 (태그 검색에 사용됨)
pin: true                            # 이 포스트를 메인 페이지에 고정
math: true                           # 이 포스트에서 수식(MathJax)을 사용
toc: true                            # 이 포스트에서 목차를 사용
# image: /assets/img/sample.png      # 썸네일 이미지 (선택 사항)
---

# 오라클 서버 준비

오라클에서 회원가입을 성공적으로 마치면 다음과 같은 메일이 옵니다.
회원가입 때 필요한 영문주소는 해당 링크에서 확인할 수 있습니다.
([우편번호](https://www.jusoen.com/addreng.asp?p1=%EC%9A%B0%ED%8E%B8%EB%B2%88%ED%98%B8))
![오라클 회원가입 메일](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719183339.png)

확인하면 다음과 같은 쿠키창이 뜨는데, 
View and change cookie preferences 를 클릭하여 필수 Cookies만 허용했습니다.

![쿠키 설정창](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719183240.png)

![쿠키 설정 옵션](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719183441.png)
최상단의 Required Coockies를 클릭 후 Submit 하면 됩니다.


![로그인 화면](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719183554.png)
그럼 사용자 계정의 이름(클라우드 이름)을 포함한 로그인 창에서 로그인이 가능합니다.

![클라우드 주소 확인](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719183650.png)
우측 상단의 클라우드 주소는 한국 춘천 데이터센터로 되어 있습니다.
회원가입 당시에 수정하지 않는 조건으로 동의하는 부분이 있었으므로 넘어가겠습니다.

Oracle 사에서는 Virtual Machine 을 인당 2개씩 무료로 제공합니다.
해당 정보는 여기서 확인할 수 있습니다.([Cloud Free Tier | Oracle 대한민국](https://www.oracle.com/kr/cloud/free/))
![Oracle Free Tier 정보](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719185707.png)

해당 링크를
[Oracle Cloud Free Tier | Oracle](https://www.oracle.com/cloud/free/?source=%3Aow%3Ao%3Ah%3Apo%3AOHPPanel1nav0625&intcmp=%3Aow%3Ao%3Ah%3Apo%3AOHPPanel1nav0625)
들어가서 옵션을 선택하면 더 많은  Free Tier 제품들을 살펴볼 수 있습니다.
이번 블로그는 AMD VM 하나를 만들어보겠습니다.

![Free Tier 제품 목록](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719185559.png)

첫 달 제공하는 300$ token은 일단 제외하고,
하나의 Free Tier VM 인스턴스를 생성해보겠습니다.
![Compute 버튼 클릭](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719183829.png)
우측 상단의 Build Tab에서 Compute 버튼을 누릅니다.

![인스턴스 설정 화면](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719184759.png)
인스턴스의 이름 설정 및 Advanced options이 있습니다.
공식 문서에는 다음 4종류의 설정을 설명하고 있습니다.

![인스턴스 타입 설명](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719185041.png)

각각의 설명은 다음과 같습니다.

| 구분 (Type)             | 핵심 특징             | 비용    | 용량 보장   | 추천 사용 사례               |
| --------------------- | ----------------- | ----- | ------- | ---------------------- |
| **온디맨드 (On-demand)**  | 사용한 만큼만 지불, 유연함   | 표준    | 보장 안 됨  | 개발, 테스트, 예측 불가능한 워크로드  |
| **선점형 (Preemptible)** | 매우 저렴하지만 강제 종료 가능 | 매우 저렴 | 보장 안 됨  | 배치 처리, 렌더링 등 중단 가능한 작업 |
| **예약 (Reserved)**     | 장기 약정으로 비용 대폭 할인  | 저렴    | **보장됨** | 안정적인 운영 서버 (웹, DB 등)   |
| **전용 (Dedicated)**    | 물리 서버 독점, 완벽한 격리  | 높음    | **보장됨** | 높은 보안, 규제 준수, 라이선스 최적화 |

프리티어는 우선 온디맨드로 시도해보겠습니다. 

아래 Image and shape에서 서버 설정을 진행할 수 있습니다!
여기서 Image란 VM 인스턴스를 생성하는데 사용되는 가상 하드 드라이버의 템플렛을 말합니다.

![이미지 선택 화면](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719200730.png)
저는 Ubuntu 22.04 버전을 사용하겠습니다.
![Ubuntu 22.04 선택](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719201246.png)

이후 Shape에 대해서는 Free에 해당하는 마지막 옵션을 골랐습니다.
![Shape 선택](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719201349.png)

이후 Networking 부분에서는 2가지를 설정할 수 있습니다.
1. 추후 Virtual Cloud Network(VCN)을 활용하기 위한 네트워크 설정,
2. SSH key setting

저는 추후 VCN 이용 계획이 없어, VINC는 VM_1로 지정했습니다.
![네트워크 설정](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719202704.png)
기존 네트워크가 없기에 새로운 네트워크와 서브넷을 등록합니다.
이후 IP 주소 관련된 설정은 해당 조건이 맞지 않아 선택하지 않고 넘어갑니다.

그리고 SSH는 제 윈도우에서 만든 키를 이미 가지고 있어서, pub 키를 등록했습니다.
![SSH 키 설정](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719202219.png)

Upload public key file을 선택한 후 제가 가진 ssh.pub 파일을 등록했습니다.

이후에 Boot volume을 조정합니다.
저는 Oracle에서 제공하는 기본 boot volume을 사용하기 위해 어떠한 설정도 바꾸지 않습니다.
사용자 지정 boot volume을 위해서는 첫번째 옵션을 켠 후 수정이 가능합니다.

![Boot Volume 설정](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719203240.png)
boot volume은 인스턴스와 별개로 앞서 선택한 Image를 복제해서 서버 사용이 가능하도록 하는 메모리 공간을 말합니다.
따라서 Free tier를 사용하는 과정에서는 상관이 없습니다.
(인스턴스를 제거해도 남아있기 때문에, 유료 요금을 사용하는 경우 반드시 불필요시 **따로 제거**해줘야 합니다. **금액이 계속 청구**됩니다.)

만약 보안이 필요한 경우나, 더 큰 부팅 볼륨이 필요하다면 해당 옵션을 조정하시면 됩니다.

![설정 검토](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719203728.png)
마지막 Review Tab에서는 상기 설정한 내용을 확인합니다.
Shape build가 요금에서 중요하기 때문에 다시 한 번 확인해줍니다.

![인스턴스 생성 완료](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719203928.png)
Create를 눌러 작업을 완료하면 최종적으로 해당 화면을 볼 수 있습니다.
우측의 Start 버튼을 누르고 상단 메뉴 중 Details Tab으로 넘어옵니다.
![인스턴스 상세 정보](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719204139.png)
해당 페이지에는 연결을 위한 IP Address가 제공되어 있기 때문에, Visual Studio Code의 SSH 확장자를 이용하면 쉽게 연결이 가능합니다.

포트는 흔히 사용되는 22번이지만, 만약 다른 포트를 사용하고 싶다면 여러 작업이 필요합니다.
(OCI - 방화벽 관련된 설정에서 OS의 방화벽을 설정할 수 있으나, 해당 글에서는 다루지 않겠습니다.)

![VSCode SSH 설정](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719205040.png)
저는 윈도우를 사용 중이며, VSC에서 SSH 파일을 설정하여 연결합니다.
아까 등록한 Pub 파일과 쌍이 되는 Private Key의 위치를 등록합니다.  

![SSH 연결 완료](/assets/img/posts/2025-07-19-OracleVM_Setting/Pasted%20image%2020250719205340.png)
등록을 마치면 home dir 내부에 ubuntu라는 폴더가 있습니다. 해당 공간을 이용하면 됩니다. 

이상으로 포스팅을 모두 마치겠습니다.