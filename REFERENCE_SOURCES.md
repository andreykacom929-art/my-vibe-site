# Эталонные источники кода и анимации

Привязка к `README.md` («Философия разработки и стандарты анимации»).
Статус форков проверен в профиле `andreykacom929-art` на 2026-09-24 (`gh repo list` + публичная страница репозиториев).

## Статус форков

| Репозиторий в README | Форк в профиле | Upstream | Изменения в форке |
| --- | --- | --- | --- |
| `airbnb/javascript` | ✅ `andreykacom929-art/Airbnb-` | `airbnb/javascript` @ `master` | нет, HEAD апстрима |
| `vercel/style-guide` | ✅ `andreykacom929-art/style-guide` | `vercel/style-guide` @ `canary` | нет |
| `codse/animata` | ✅ `andreykacom929-art/animata` | `codse/animata` @ `main` | нет |
| `radix-ui/primitives` | ✅ `andreykacom929-art/primitives` | `radix-ui/primitives` @ `main` | нет |
| `Thakuma07/Truus.co-Awwward-Website` | ❌ **отсутствует** | публичный upstream существует | — |
| `greensock/GSAP` (в README не упомянут) | ✅ `andreykacom929-art/GSAP` | `greensock/GSAP` @ `master` | нет |

Итого в профиле 6 репозиториев: `my-vibe-site` + 5 форков. Форка Truus среди них нет.

## 1. Стандарты кода

### `andreykacom929-art/Airbnb-` → правило README «не использовать легаси, Airbnb JS Style Guide»
- `react/README.md` — раздел по React: компоненты, JSX, `props`, порядок методов.
- `packages/eslint-config-airbnb/rules/react.js` — что именно линтер считает правильным React-кодом.
- `packages/eslint-config-airbnb/rules/react-hooks.js` — правила хуков (порядок, зависимости) → «динамические значения выноси в кастомные хуки».
- `packages/eslint-config-airbnb/rules/react-a11y.js` — доступность интерактивных элементов.
- `packages/eslint-config-airbnb-base/rules/es6.js`, `rules/style.js`, `rules/variables.js` — запрет легаси-методов, именование.
- `packages/eslint-config-airbnb/hooks.js`, `index.js` — точка входа конфига для проекта.

### `andreykacom929-art/style-guide` (Vercel) → правило README «архитектурные гайдлайны Vercel»
- `eslint/react.js`, `eslint/next.js`, `eslint/typescript.js`, `eslint/_base.js` — сборка конфига.
- `eslint/rules/react.js`, `eslint/rules/import.js`, `eslint/rules/stylistic.js` — правила стиля и импортов.
- `prettier/index.js` — форматирование (эталон отступов/переносов).
- `typescript/tsconfig.base.json` — базовая конфигурация TS.
- `.editorconfig` — сквозные настройки редактора.

## 2. Анимации и микро-взаимодействия

### `andreykacom929-art/animata` → «естественная физика движения», микро-взаимодействия 150–200 ms
- `animata/text/spring-scale-in.tsx` — эталон spring-физики без линейных анимаций.
- `animata/text/split-text.tsx`, `text/staggered-letter.tsx`, `text/per-character-rise.tsx`, `text/per-word-crossfade.tsx` — тайминги и stagger для текстовых слоев.
- `animata/text/mask-reveal-up.tsx`, `text/scroll-reveal.tsx`, `text/wave-reveal.tsx` — reveal-паттерны под скролл.
- `animata/text/ticker.tsx`, `text/swap-text.tsx`, `text/typing-text.tsx`, `text/gibberish-text.tsx` — цикличные микровзаимодействия.
- `animata/scroll/stacked-sections.tsx` + `stacked-sections.css` — эталон «сложного скролла» со слоями и `will-change`.
- `animata/preloader/split-reveal/index.tsx`, `root.tsx`, `context.tsx`, `progress.tsx`, `overlay.tsx`, `types.ts` — эталон **структуры кода**: разделение логики (context/execute-task/preload-images) и представления (overlay/progress-count/shutter).
- `animata/container/marquee.tsx` + `.css`, `container/cursor-tracker.tsx`, `container/animated-dock.tsx`, `container/animated-border-trail.tsx` — микро-взаимодействия в 150–200 ms.
- `animata/card/tilted-card.tsx`, `card/staggered-card.tsx`, `card/flip-card.tsx`, `card/blur-stack-card.tsx` — **асимметричные карточки вместо шаблонных**.
- `animata/background/*` — `interactive-grid.tsx`, `animated-beam.tsx`, `blurry-blob.tsx`, `moving-gradient.tsx`, `dot.tsx`, `grid.tsx` — фоновые слои.
- `animata/hero/hero-section.tsx`, `hero/shape-shifter.tsx`, `hero/hero-section-text-hover.tsx` — первый экран.
- `animata/image/images-reveal.tsx`, `image/disclose-image.tsx`, `list/reveal-image.tsx` — работа с медиа.
- `hooks/use-prefers-reduced-motion.ts` — обязательный a11y-гейт для всех анимаций.
- `hooks/use-mouse-position.ts`, `hooks/use-exit-intent.ts`, `hooks/use-lock-body.ts`, `hooks/use-media-query.ts`, `hooks/use-mounted.ts` — **эталон кастомных хуков** (вынос динамики из компонентов).
- `lib/utils.ts` — `cn()` и утилиты классов.
- `app/(main)/_landing/home-page.tsx`, `stats-bento.tsx`, `testimonials.tsx`, `faq-section.tsx`, `call-to-action.tsx`, `newsletter.tsx` — эталон композиции страницы из секций.
- `components/ui/*` (button, dialog, tooltip, popover, scroll-area, tabs) — база под интерактив.

### `andreykacom929-art/primitives` (Radix) → доступное поведение под кастомную анимацию
- `packages/react/presence/src/presence.tsx` + `use-state-machine.tsx` — **эталон архитектуры exit-анимаций** (unmount только после завершения анимации).
- `packages/react/scroll-area/src/scroll-area.tsx`, `use-state-machine.ts` — виртуализация/кастомный скролл.
- `packages/react/portal/src/portal.tsx`, `slot/src/slot.tsx`, `direction/src/direction.tsx` — примитивы композиции.
- `packages/react/focus-scope/src/focus-scope.tsx`, `dismissable-layer/src/dismissable-layer.tsx` — фокус и закрытие оверлеев (модалки/меню).
- `packages/react/popper/src/popper.tsx`, `popover/src/popover.tsx`, `tooltip/src/tooltip.tsx`, `hover-card/src/hover-card.tsx`, `toast/src/toast.tsx` — попперы и всплывающие слои.
- `packages/react/collection/src/collection.tsx` — управление списками детей.
- `packages/react/use-controllable-state/src/use-controllable-state.tsx`, `use-size/src/use-size.tsx`, `use-previous/src/use-previous.tsx`, `use-rect/src/use-rect.tsx`, `use-callback-ref/*`, `use-layout-effect/*` — паттерн кастомных хуков продакшн-уровня.
- `packages/react/compose-refs/src/compose-refs.tsx`, `context/src/create-context.tsx` — glue-код.

### `andreykacom929-art/GSAP` (в README не указан, но нужен под ScrollTrigger)
- `src/ScrollTrigger.js` — архитектура скролл-триггеров: `refresh()`, `matchMedia`, `kill()` для таймлайнов.
- `src/ScrollSmoother.js` — инерционный скролл («чувство веса»).
- `src/InertiaPlugin.js`, `src/utils/VelocityTracker.js` — инерция и физика движения.
- `src/Observer.js` — тач/скролл-наблюдатели (момент `kill()` при размонтировании).
- `src/gsap-core.js`, `src/CSSPlugin.js` — корректная работа с `transform` и `will-change`.
- `src/Flip.js` — FLIP-переходы раскладки, `src/CustomEase.js` — кастомные кривые, `src/SplitText.js` — разбивка текста.

## 3. Дисциплина сетки и типографики
- `style-guide/prettier/index.js` + `.editorconfig` — единый формат.
- `animata/lib/brand-font.ts` — подключение шрифтов (fluid typography).
- `animata/app/(main)/_landing/*` — примеры асимметричной бенто-раскладки вместо шаблонных карточек.

## 4. Truus — только вдохновение, без копирования кода

Решение: форка нет, поэтому `Thakuma07/Truus.co-Awwward-Website` используется как read-only источник идей (смотрели README + дерево файлов + код компонентов). Стек: Next.js 15 + React 19, GSAP (ScrollTrigger + InertiaPlugin), Lenis, vanilla CSS с CSS-переменными, централизованные данные в `lib/data.js`.
**Важно:** у репозитория нет файла LICENSE (190 ★, `license: NONE`) → код под всеобщим авторским правом. Копировать нельзя, можно только переосмыслять приёмы.

### Приёмы, которые берём как идею (переписать под свой проект)
- `components/SmoothScroll.jsx` — Lenis, сшитый с `gsap.ticker` (`lenis.raf(time * 1000)` + `lagSmoothing(0)`) и `lenis.on('scroll', ScrollTrigger.update)` → «чувство веса» при скролле.
- `components/HorizontalWords.jsx` — пининг секции через `scrollTrigger` с `start: "top bottom"`, `end: () => ...`, `scrub: 1`, `invalidateOnRefresh: true` и функциями вместо значений → корректный ресайз. Плюс `gsap.context(...)` + `return () => ctx.revert()` — совпадает с требованием `kill()` из README.
- `components/MotionCards.jsx` — InertiaPlugin: замер скорости курсора по `mousemove`, на `mouseleave` старт `inertia` с `velocity` и возвратом в `end` (исходные `x/y/rotation` из `gsap.getProperty`) → эталон «флинга» тяжёлых объектов.
- `components/Footer.jsx`, `Navbar.jsx` — proximity push стикеров по скорости свайпа + `WIGGLE_CONFIG` (один конфиг на все wiggle) + `steps(1) yoyo`.
- `components/CursorBubble.jsx`, `VimeoHero.jsx` — курсорный blob на `gsap.quickTo` (вместо `gsap.to` в каждом кадре).
- `components/TransitionScribble.jsx` — полноэкранный SVG-скрайбл маской, дро/ан-дро через `stroke-dasharray`.
- `components/SvgSymbols.jsx` — скрытые `<symbol>` defs: спрайт вместо дублирования SVG.
- `lib/data.js` — все статические данные (бренды, карточки, конфиги) одним модулем → логика данных отделена от разметки (совпадает с п.1 README).
- `app/globals.css` + `app/styles/*.css` (11 партиалов), `app/styles/base.css` — токены дизайна на CSS-переменных.
- `components/ServiceCards.jsx` — веер карточек на hover через elastic-ease + мобильный стек на ScrollTrigger.
- Идея «строить секцию как изолированный компонент + отдельный CSS-партиал + данные из `lib/`» → берём как схему структуры сайта.

### Где Truus **не** эталон (делаем лучше, по README)
- `will-change: transform` в репозитории не используется **вообще** (проверено `grep -r` по `app/styles` и `components`) — у нас обязателен для анимируемых слоев.
- В `MotionCards.jsx` / `HorizontalWords.jsx` выборка через глобальные `document.querySelectorAll('.motion-card__card')` вместо scoped-ref внутри `gsap.context` → у нас только refs/скоупы.
- `DoubleMarquee.jsx:88` чистит триггеры глобальным перебором `ScrollTrigger.getAll().forEach(t => t.kill())` с фильтром по строке `.Double-marquee` → у нас только `ctx.revert()` / собственный таймлайн.
- `SmoothScroll.jsx` прячет инстанс в `window.__lenis` для доступа из других компонентов → у нас React-контекст или хук, без глобалов.
- Fluid typography почти не применена: `clamp()`/`vw` найдены только в `vimeo-hero.css` → у нас типографика и отступы завязаны на viewport (п.3 README).
- Компоненты-«монолиты» (300+ строк GSAP в одном файле) → у нас логика движения выносится в кастомные хуки.
