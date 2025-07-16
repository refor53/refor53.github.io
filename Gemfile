# Gemfile (최종 동기화 버전)

# frozen_string_literal: true

source "https://rubygems.org"

# 1. Jekyll 블로그 엔진
gem "jekyll", "~> 4.3"

# 2. Chirpy 테마
gem "jekyll-theme-chirpy", "~> 7.3.0"

# 3. _config.yml에 명시된 모든 플러그인
#    '요구사항'과 '설치 목록'을 완전히 일치시킵니다.
gem "jekyll-paginate", "~> 1.1"
gem "jekyll-seo-tag", "~> 2.8"
gem "jekyll-archives", "~> 2.2"
gem "jekyll-sitemap", "~> 1.4.0"         # ★ 누락되었던 플러그인
gem "jekyll-redirect-from", "~> 0.16.0"   # ★ 에러를 일으킨 플러그인
gem "jekyll-feed", "~> 0.17.0"
gem "jekyll-include-cache", "~> 0.2"

# 4. SASS 버전 충돌 해결
gem "jekyll-sass-converter", "~> 3.0"

# 5. JSON 버전 고정 (SASS 호환성)
gem "json", "~> 2.6"

# 6. 로컬 개발 환경용 플러그인
group :jekyll_plugins do
  gem "jekyll-watch", "~> 2.2.1"
end

# 7. Windows 플랫폼용 설정 (WSL에서는 무시됨)
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
  gem "wdm", "~> 0.2.0"
end