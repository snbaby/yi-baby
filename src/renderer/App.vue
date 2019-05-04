<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
  const puppeteer = require('puppeteer')
  const devices = require('puppeteer/DeviceDescriptors')
  const iPhone = devices['iPhone X']
  const sleep = function (ms) {
    return new Promise((resolve) => setTimeout(resolve, ms))
  }
export default {
    name: 'yi-baby',
    data () {
      return {
        cookies: []
      }
    },
    created () {
      const self = this
      console.log('created');
      (async () => {
        console.log('browser')
        const browser = await puppeteer.launch({
          headless: false,
          executablePath: `${process.cwd()}\\resources\\app.asar.unpacked\\node_modules\\puppeteer\\.local-chromium\\win64-650583\\chrome-win\\chrome.exe`,
          defaultViewport: {
            width: 1280,
            height: 800,
            deviceScaleFactor: 1,
            isMobile: true,
            hasTouch: true
          }
        })
        console.log('newPage')
        const page = await browser.newPage()
        console.log('baidu')
        await page.goto('https://login.taobao.com/member/login.jhtml')
        await page.screenshot({path: 'yqq.png'})
        await page.waitForNavigation({
          waitUntil: 'load'
        })
        await page.emulate(iPhone)
        await page.goto('https://detail.m.tmall.com/item.htm?id=589642682816&skuId=4030323836570&decision=sku')
        console.log('waitForSelector buy')
        await page.waitForSelector('body > div.widgets-cover.show > div.cover-content > div > div.body')
        console.log('tap buy')
        await sleep(2000)
        await page.tap('body > div.widgets-cover.show > div.cover-content > div > div.footer.trade > a.buy')
        console.log('tap submitOrder_1')
        await page.waitForSelector('#submitOrder_1 > div.mui-flex.align-center > div.cell.fixed.action > div')
        await page.tap('#submitOrder_1 > div.mui-flex.align-center > div.cell.fixed.action > div')
        await page.waitForSelector('#cashierPreConfirm > div.am-section')
        let order = await page.evaluate(() => {
          return 'https://h5.m.taobao.com/mlapp/odetail.html?bizOrderId=' + window.location.href.substring(window.location.href.indexOf('pay_order_id=') + 13, window.location.href.indexOf('&show_url='))
        })
        await page.goto(order)
        await page.waitForSelector('body > div > div.main-layout > div:nth-child(9) > div > div:nth-child(2) > div:nth-child(3)')
        await page.tap('body > div > div.main-layout > div:nth-child(9) > div > div:nth-child(2) > div:nth-child(3)')
        await page.waitForSelector('[name=\'peerPayerEmail\']')
        await sleep(1000)
        await page.type('body > article > form > div > input[type="text"]', 'sn_baby@qq.com', { delay: 200 })
        await page.tap('body > article > form > input.btn.btn-ok')
        self.cookies = await page.evaluate(() => {
          return document.cookie
        })
      })()
    }
  }
</script>

<style>
  /* CSS */
</style>
