<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
  const puppeteer = require('puppeteer')
  export default {
    name: 'yi-baby',
    created () {
      console.log('created');
      (async () => {
        console.log('browser')
        const browser = await puppeteer.launch({
          headless: false,
          executablePath: `${process.cwd()}\\resources\\app.asar.unpacked\\node_modules\\puppeteer\\.local-chromium\\win64-650583\\chrome-win\\chrome.exe`
        })
        console.log('newPage')
        const page = await browser.newPage()
        console.log('baidu')
        await page.goto('https://www.baidu.com')
        await page.screenshot({path: 'yqq.png'})
      })()
    }
  }
</script>

<style>
  /* CSS */
</style>
