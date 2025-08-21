# Digital Coupon Clippers

Automated JavaScript bookmarklets for clipping digital coupons from CVS and Publix. **Does not work on mobile browsers.**

### 🔗 Copy & Paste Bookmarklet Code

**CVS Clipper**: 
```javascript
javascript:(async()=>{const delay=ms=>new Promise(r=>setTimeout(r,ms)),scrollDelay=1000,clipDelay=2000;let clipped=0,scrollCount=0;const isAtBottom=()=>(window.innerHeight+window.scrollY)>=document.body.offsetHeight-100;console.log("📜 CVS Clipper started...");while(!isAtBottom()&&scrollCount<50){let coupons=[...document.querySelectorAll("button.coupon-action.button-blue.sc-send-to-card-action")];for(let btn of coupons){if(btn.offsetParent!==null&&!btn.disabled){try{btn.scrollIntoView({behavior:"smooth",block:"center"});btn.click();clipped++;console.log(`🔘 Clipped #${clipped}`);await delay(clipDelay);}catch(e){console.warn("⚠️ Clip failed:",e);}}}scrollCount++;window.scrollBy(0,500);await delay(scrollDelay);console.log(`📍 Scroll ${scrollCount}, at bottom: ${isAtBottom()}`);}console.log(`🎉 Done! Clipped ${clipped} coupons.`);alert(`🎉 Done!\nYou clipped ${clipped} new coupon${clipped===1?"":"s"}.`);})();
```

**Publix Clipper**: 
```javascript
javascript:(async()=>{console.log('🟢 Publix Clipper started');const delay=t=>new Promise(r=>setTimeout(r,t));const randomDelay=(min,max)=>delay(Math.floor(Math.random()*(max-min+1))+min);let clipped=0;const scrollToEl=e=>e.scrollIntoView({behavior:'smooth',block:'center'});const humanClick=async(btn)=>{const rect=btn.getBoundingClientRect();const x=rect.left+rect.width*0.5+Math.random()*10-5;const y=rect.top+rect.height*0.5+Math.random()*10-5;btn.focus();btn.dispatchEvent(new MouseEvent('mouseover',{bubbles:true,clientX:x,clientY:y}));await delay(50);btn.dispatchEvent(new MouseEvent('mousedown',{bubbles:true,clientX:x,clientY:y}));await delay(50);btn.dispatchEvent(new MouseEvent('mouseup',{bubbles:true,clientX:x,clientY:y}));btn.click();};async function clickLoadMoreAndWait(){const btn=document.querySelector('button[data-qa-automation="button-Load more"]');if(!btn)return false;console.log('⬇️ Load more found, clicking...');scrollToEl(btn);await humanClick(btn);window.scrollTo(0,document.body.scrollHeight);let retries=10,last=0;while(retries-->0){await delay(1000);let current=Array.from(document.querySelectorAll('button[aria-label="Clip coupon"]')).filter(e=>'false'===e.getAttribute('aria-checked')).length;if(current>last){console.log(`✅ Found ${current} coupons after load.`);return true;}}console.log('❌ No new coupons after Load more.');return false;}let pass=0,maxPasses=25;for(;pass++<maxPasses;){let buttons=Array.from(document.querySelectorAll('button[aria-label="Clip coupon"]')).filter(e=>'false'===e.getAttribute('aria-checked'));console.log(`🔍 Pass ${pass}: ${buttons.length} unclipped coupons`);if(buttons.length===0){const loaded=await clickLoadMoreAndWait();if(!loaded)break;}else{for(const btn of buttons){scrollToEl(btn);try{await humanClick(btn);clipped++;console.log(`🧾 Clipped #${clipped}`);await randomDelay(250,400);}catch(e){console.warn('❌ Failed to click:',e);}}}}console.log(`✅ Publix Clipper finished. Total clipped: ${clipped}`);alert(`✅ Publix Clipper finished. Total clipped: ${clipped}`);})();
```

### Installation Instructions:
1. **Copy** the entire code block above (or appropriate .txt file)
2. **Right-click your bookmarks bar** → "Add page" or "Add bookmark"
3. **Name**: Enter "CVS Clipper" or "Publix Clipper"
4. **URL**: Paste the copied JavaScript code (starting with `javascript:`)
5. **Save the bookmark**

## How to Use

1. Navigate to the store's digital coupon page and sign in
2. Click your bookmarklet in the bookmarks bar
3. Watch the automation run (check browser console for progress)
4. Wait for completion alert showing total coupons clipped

## Legal Disclaimer

These bookmarklets are provided for educational and personal use only. Users are responsible for:

- Ensuring compliance with store Terms of Service
- Respecting website usage policies  
- Using automation responsibly and ethically

**Use at your own discretion and risk.**

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.