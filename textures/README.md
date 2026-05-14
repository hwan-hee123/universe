# 고해상도 행성 텍스처 (Solar System Scope)

이 폴더에 **Solar System Scope** (CC BY 4.0) 2k 텍스처를 넣으면 자동으로
1k 기본 텍스처 대신 사용됩니다. 다운로드 안 한 파일은 자동으로 기존
1k 텍스처(jsDelivr CDN)로 폴백되므로 부분적으로만 다운로드해도 동작합니다.

## 다운로드

https://www.solarsystemscope.com/textures/

페이지에서 개별 텍스처를 우클릭 → "이미지 저장"하거나, 전체 ZIP 패키지를
받아서 압축을 풉니다. 라이선스: **CC BY 4.0** (출처 표기만 하면 자유 사용).

## 이 폴더에 필요한 파일

기본 2k 권장 (행성당 1~3 MB 정도). 원하면 8k도 OK.

```
textures/
├── 2k_sun.jpg
├── 2k_mercury.jpg
├── 2k_venus_atmosphere.jpg     ← 시각광 (구름)
├── 2k_venus_surface.jpg        ← 또는 레이더 표면 (디테일 풍부)
├── 2k_mars.jpg
├── 2k_jupiter.jpg
├── 2k_saturn.jpg
├── 2k_saturn_ring_alpha.png    ← 토성 고리
├── 2k_uranus.jpg
├── 2k_neptune.jpg
├── 2k_moon.jpg                 ← 지구의 달
├── (선택) 2k_stars_milky_way.jpg  ← 우주 배경에 우리은하 panorama
└── (선택) 2k_earth_nightmap.jpg, 2k_earth_clouds.jpg 등
```

`2k_stars_milky_way.jpg`가 있으면 우주 배경에 우리은하가 둘러싸이게 표시됩니다.
없으면 별필드와 외부 은하 sprite만 표시되며 페이지는 정상 동작.

## 외부 은하 사진 (선택, 권장)

`textures/galaxies/` 폴더에 갤럭시 사진을 넣으면 절차적 입자 대신
실제 사진을 sprite로 표시합니다. 첨부된 안드로메다 사진처럼
사실적인 갤럭시 모습이 됩니다.

```
textures/galaxies/
├── M31.jpg     ← 안드로메다 은하
├── M33.jpg     ← 삼각형자리 은하
├── M51.jpg     ← 소용돌이 은하
├── M104.jpg    ← 솜브레로 은하
├── LMC.jpg     ← 대마젤란 은하
└── SMC.jpg     ← 소마젤란 은하
```

각 파일 약 1~2MB (1k~2k 해상도 권장).

### 공개 이미지 출처

NASA / ESA / Hubble / Wikipedia Commons 모두 공개 (Public Domain 또는 CC BY).

직접 검색하거나 아래 페이지에서 다운로드:

- **Wikipedia Commons** — 'Andromeda Galaxy', 'M51', 'M104 Sombrero' 등 검색
  - https://commons.wikimedia.org/
- **NASA Hubble Heritage** — https://hubblesite.org/images/gallery
- **ESO Public Images** — https://www.eso.org/public/images/

### 활성화

다운받아서 위 파일명으로 폴더에 두기만 하면 자동 적용.
파일이 없는 갤럭시는 절차적 입자(현재)로 표시됨 → 부분만 적용도 OK.

지구 본체는 이미 turban/webgl-earth 4k를 CDN으로 받아오므로 별도 파일 불필요.

## 활성화

코드 안의 `USE_HIRES_TEXTURES` 값을 `true`로 바꿔주세요.
`index.html` 안에서 검색해서 한 줄 수정:

```js
const USE_HIRES_TEXTURES = true;  // ← false였던 걸 true로
```

페이지 새로고침하면 적용됩니다.

## 작동 방식

- `USE_HIRES_TEXTURES = true`인 상태에서 `textures/2k_mars.jpg`가 있으면 → 그걸 사용
- 파일이 없으면 → 콘솔에 경고 후 기존 1k CDN으로 자동 폴백
- `USE_HIRES_TEXTURES = false`로 두면 → 무조건 1k CDN 사용 (지금까지 동작)

따라서 안전합니다. 다운로드 안 해도 작동, 일부만 다운로드해도 작동.

## 저장소 크기 주의

2k 텍스처 10개 = 약 15~25MB. GitHub repo에 commit하면 push에 시간이
좀 걸릴 수 있습니다. 8k는 100MB 이상이라 권장 안 함.

너무 큰 파일이 부담이면 `.gitignore`에 추가해서 본인 PC에만 두고 써도 됩니다
(다른 사람이 clone하면 1k 폴백 자동 사용).
