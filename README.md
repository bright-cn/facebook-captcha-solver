# Facebook 验证码解决方案  

[![Promo](https://github.com/luminati-io/LinkedIn-Scraper/raw/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://www.bright.cn/products/web-unlocker/captcha-solver/facebook)

使用 Bright Data 先进的 CAPTCHA 解决技术，轻松绕过 Facebook 验证码。通过机器学习算法、[自动化 IP 轮换](https://www.bright.cn/solutions/rotating-proxies)以及强大的代理基础设施，确保在目标网站上获得无缝且持续的访问。  

Bright Data 的 CAPTCHA Solver 是我们 [**抓取浏览器**](https://www.bright.cn/products/scraping-browser) 和 [**网络解锁器 API**](https://www.bright.cn/products/web-unlocker) 的内置功能，可全面应对最复杂的验证码挑战。  

## 功能  
- **快速验证码解决**: 以高精度和高速度自动解决 Facebook 验证码。  
- **IP 轮换**: 通过自动重试和动态 IP 调整来避免被封禁。  
- **浏览器指纹**: 模拟真实用户行为，[绕过复杂的机器人检测](https://www.bright.cn/blog/web-data/anti-scraping-techniques)。  
- **JavaScript 渲染**: 应对高度依赖 JavaScript 的网站中的动态内容。  
- **全球范围覆盖**: 精准覆盖全球任何地区，解锁相关内容。  
- **无缝集成**: 可与 Puppeteer、Playwright 和 Selenium 等工具轻松协作。  
- **事件监控**: 监控验证码解决过程中的检测、成功或失败等事件。  

## 为什么选择 Facebook 验证码解决方案  

### **全球超过 20,000 名客户的信赖**  
Bright Data 的 CAPTCHA Solver 以其无与伦比的可靠性和性能，获得了开发者、企业及各类公司的广泛信任。  

### **倚靠高端代理网络支持**  
拥有超过 1 亿个 IP 地址及高级地理定位功能，我们的代理基础设施可确保验证码解决过程顺畅无阻。  

### **AI 驱动的验证码解决**  
我们的 CAPTCHA Solver 使用基于 AI 的高级逻辑来自动检测、分析并解决验证码。它还可通过重试、指纹模拟和请求头处理，绕过最复杂的反机器人机制。  

### **专为开发者打造**  
- 可轻松与 Puppeteer、Playwright 和 Selenium 整合。  
- 可全面自定义验证码解决的相关配置。  
- 支持自动重试和动态 IP 调整，确保数据抓取不中断。

> **提示 💡**  
>> 已经有自己的验证码解决方案？可结合我们的 [Puppeteer](https://www.bright.cn/integration/puppeteer)、[Playwright](https://www.bright.cn/integration/playwright) 和 [Selenium](https://www.bright.cn/integration/selenium) 代理，大幅减少 CAPTCHA 出现概率。

## 工作原理  

Bright Data 的 CAPTCHA Solver 已集成在 **Scraping Browser** 和 **Web Unlocker** 中，让验证码解决变得轻而易举。  

### **自动验证码解决**  
CAPTCHA Solver 能实时自动检测并解决验证码。只需启用该功能，即可从检测到解决全程自动化。  

### **针对 Facebook 验证码挑战的自定义选项**  
```javascript
// 为不同类型的验证码定义默认配置
function getCaptchaOptions(captchaType, customOptions = {}) {
  const defaultOptions = {
    timeout: 30000, // 等待验证码解决的最大时间（毫秒）
    check_timeout: 500, // 检查验证码状态的间隔（毫秒）
    wait_networkidle: { timeout: 1000 }, // 等待网络空闲 1 秒
    debug: false // 调试模式（默认关闭）
  };

  // 定义针对特定验证码的选择器
  const captchaSelectors = {
    DataDome: { selector: '#datadome-captcha', success_selector: '#captcha-success' },
    reCAPTCHA: { selector: '.g-recaptcha', success_selector: '.recaptcha-success' },
    ClickCaptcha: { selector: '.click-captcha', success_selector: '.captcha-passed' },
    hCaptcha: { selector: '.h-captcha', success_selector: '.hcaptcha-success' },
    PerimeterX: { selector: '#px-captcha', success_selector: '#px-success' },
    SimpleCaptcha: { selector: '.simple-captcha', success_selector: '.captcha-done' },
    FunCaptcha: { selector: '.funcaptcha', success_selector: '.funcaptcha-success' },
    CloudflareTurnstile: { selector: '.cf-turnstile', success_selector: '.cf-success' },
    AWSWAF: { selector: '#aws-waf-captcha', success_selector: '#aws-waf-success' },
    GeeTest: { selector: '.geetest-captcha', success_selector: '.geetest-success' },
    KeyCAPTCHA: { selector: '#keycaptcha', success_selector: '#keycaptcha-success' },
    PuzzleCAPTCHA: { selector: '.puzzle-captcha', success_selector: '.puzzle-solved' },
    YandexCAPTCHA: { selector: '#yandex-captcha', success_selector: '#yandex-success' },
    ImageCAPTCHA: { selector: '.image-captcha', success_selector: '.image-captcha-success' },
    TextCAPTCHA: { selector: '.text-captcha', success_selector: '.text-captcha-success' }
  };

  // 为给定的验证码类型获取正确的选择器
  const selectedOptions = captchaSelectors[captchaType] || {};

  // 将默认选项、验证码特定选项和自定义配置合并
  return { ...defaultOptions, ...selectedOptions, ...customOptions };
}

// 针对不同验证码类型的使用示例
const ddOptions = getCaptchaOptions('DataDome', { timeout: 40000, debug: true });
const recaptchaOptions = getCaptchaOptions('reCAPTCHA', { debug: true });
const hcaptchaOptions = getCaptchaOptions('hCaptcha');

console.log(ddOptions);
console.log(recaptchaOptions);
console.log(hcaptchaOptions);

// 错误处理示例
try {
  if (!document.querySelector(ddOptions.selector)) {
    throw new Error(`未找到验证码元素，使用选择器: ${ddOptions.selector}`);
  }

  // 你的验证码解决逻辑
  solveCaptcha(ddOptions);
} catch (error) {
  console.error('解决验证码失败:', error.message);
}
```

#### 示例流程:  
1. **检测验证码**: 程序识别验证码类型（例如 PerimeterX）。  
2. **解决验证码**: 利用 AI 驱动的逻辑来解决验证码。  
3. **失败后重试**: 如果无法解决，系统将自动使用新 IP 重试。  
4. **返回结果**: 验证码解决成功后，系统会为目标站点提供无缝访问。  

## 支持的验证码类型  

Bright Data 的 CAPTCHA Solver 支持各种验证码类型，包括:  

- [**DataDome**](https://www.bright.cn/products/web-unlocker/captcha-solver/datadome)  
- [**reCAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/recaptcha)  
- [**Click Captcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/click-captcha)  
- [**Cloudflare**](https://www.bright.cn/products/web-unlocker/captcha-solver/Cloudflare)  
- [**PerimeterX**](https://www.bright.cn/products/web-unlocker/captcha-solver/perimeterx)  
- [**SimpleCaptcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/simplecaptcha)  
- [**FunCaptcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/funcaptcha)  
- [**Cloudflare Turnstile**](https://www.bright.cn/products/web-unlocker/captcha-solver/cloudflare-turnstile)  
- [**AWS WAF Captcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/aws-waf-captcha)  
- [**GeeTest CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/geetest-captcha)  
- [**KeyCAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/keycaptcha)  
- [**Puzzle CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/puzzle-captcha)  
- [**Yandex CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/yandex-captcha)  
- [**Image CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/image-captcha)  
- [**Text CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/text-captcha)

## 高级自定义  

[Bright Data 的 CAPTCHA Solver](https://github.com/bright-cn/Captcha-solver) 支持高级自定义，可针对特定需求对解决逻辑进行精细调整。

## 事件监控  
跟踪验证码解决事件，以便应对高级用例：  
- `Captcha.detected`: 检测到验证码并开始解决。  
- `Captcha.solveFinished`: 验证码解决成功。  
- `Captcha.solveFailed`: 验证码解决失败。  

## 价格  

| **Plan**       | **价格（每 1K 结果）** | **每月费用**  | **描述**                               |  
|----------------|------------------------|--------------|----------------------------------------|  
| **Pay-as-you-go** | $1.50                | 无需承诺     | 适用于临时的抓取需求。                 |  
| **Growth**     | $1.27                 | $499         | 为扩张中的团队度身定制。               |  
| **Business**   | $1.12                 | $999         | 适合大规模抓取操作。                   |  
| **Premium**    | $1.05                 | $1,999       | 高级功能并具备优先支持。               |  
| **Enterprise** | 定制报价              | 联系我们     | 为顶尖业务需求定制的方案。             |  

🚀 **特别优惠**: 我们将匹配您首次充值的金额，最高可达 **$500**！  

## 为什么开发者喜欢 Facebook 验证码解决方案  
- **轻松集成**: 可无缝兼容 Puppeteer、Playwright 和 Selenium。  
- **先进的 AI 逻辑**: 自动处理重试、验证码解决、指纹模拟、IP 轮换和高级请求头等。  
- **内置浏览器**: 无需管理额外的浏览器即可渲染 JavaScript。  
- **实时洞察**: 通过实时仪表板监控网络性能。  
- **强大的支持**: 24/7 全球客户支持，功能持续更新。  

## 常见问题  

### Facebook 验证码解决方案如何工作？  
该方案使用基于 AI 的高级逻辑来自动检测并解决 Facebook 验证码。  

### 是否可以同时处理多个验证码？  
可以，该方案可同时处理多种验证码类型，确保访问不中断。  

### 如果验证码解决失败，会发生什么情况？  
系统会自动重试。如果仍有问题，可随时联系我们 24/7 的支持团队进行排查。  

---

## 告别 Facebook 验证码  
立即开始免费试用，体验无缝的 [Bright Data Facebook 验证码解决方案](https://www.bright.cn/products/web-unlocker/captcha-solver/facebook)！
