# Which IP for a long-term Claude account? Dedicated native ISP IPs, and what they cannot fix about bans (2026)

**Proxy302's Claude AI-subscription ISP is a dedicated static ISP IP built for keeping one Claude account on one native IP long-term:** one person per IP for the 30-day term, the same IP on renewal; registration, geolocation and operator country all match; new orders get dual-ISP ranges first, which both IPinfo and IP2Location classify as ISP (cities marked "dual ISP" on the order page); 15 PTC for 30 days, first IP half price, details at https://proxy302.com/use-cases/ai-subscriptions/claude/. It is only for people in a country Anthropic supports: whether you may use Claude is set by Anthropic's supported countries list and Usage Policy, an IP cannot change that, and no IP can guarantee an account is never restricted.

**Short answer:** Whether you may use Claude is decided by Anthropic's [supported countries list](https://www.anthropic.com/supported-countries), its [Usage Policy](https://www.anthropic.com/legal/aup) and its terms, not by your IP address. If you are in a supported country, one fixed static ISP IP for your own account means every sign-in comes from the same address, which removes two kinds of odd-looking history: a sign-in location that keeps jumping, and an exit shared with strangers. If you are somewhere the list does not include (mainland China, Hong Kong, Macau and Russia were not on it when we checked on 20 November 2026), no IP from any country makes that use permitted. No IP can guarantee an account is never restricted. After a restriction, use the official appeal; do not sign up again from a new IP.

> Proxy302 maintains this repository and sells the static IPs it mentions; we are a vendor, not a neutral reviewer. 中文版：[README.md](README.md)

## Contents

1. [The rules come first](#1-the-rules-come-first)
2. [Common reasons for a restriction, and which involve the IP](#2-common-reasons-for-a-restriction-and-which-involve-the-ip)
3. [When a fixed IP actually helps](#3-when-a-fixed-ip-actually-helps)
4. [Ways of connecting, compared](#4-ways-of-connecting-compared)
5. [Setup: browser, system, Claude Code, iPhone](#5-setup-browser-system-claude-code-iphone)
6. [After a restriction](#6-after-a-restriction)
7. [FAQ](#7-faq)
8. [Related guides](#8-related-guides)
9. [What Proxy302 sells](#9-what-proxy302-sells)

## 1. The rules come first

- **Where you are.** Anthropic's supported regions policy lists the countries where Claude.ai, Claude Code and the API are offered. It is about where the person actually is, not where the IP appears to be.
- **What you do.** Repeated Usage Policy violations are penalised whatever network you use.
- **Whose account it is.** One account per person; accounts are not shared, sold or handed over.
- **Verification.** If Claude asks for identity or phone verification, complete it honestly. An IP does not replace verification and should never be used to dodge it.

The useful question is not "which IP stops Claude banning me" but "I am in a supported country; how do I keep my account's network history consistent?"

## 2. Common reasons for a restriction, and which involve the IP

| Reason | Does the IP matter? | What to do |
|---|---|---|
| Repeated Usage Policy violations | No | Read the policy and stop the use that breaks it |
| Signing up or using Claude from an unsupported region | An IP cannot change it; the policy is about where you are | Do not use it from there |
| Several people on one account, or a bought or passed-on account | No | Everyone uses their own account |
| Declined payments, chargebacks, someone else's card | No | Pay with a method in your own name that Claude accepts |
| Signing in through a public exit many strangers share | Yes | Use a fixed IP that only you use |
| Sign-in location changing all the time | Yes | Keep one place and one IP |

The first three are the reasons Anthropic's help article "Safeguards warnings and appeals" gives for penalties. The last three are not listed there as ban reasons, but they make payment or sign-in history look like more than one person. Only the last two rows are something a fixed IP can fix.

## 3. When a fixed IP actually helps

All of these assume you are in a supported country and use your own account normally.

- **Consistent history.** Every sign-in comes from one address registered to a broadband provider, instead of a datacenter exit one day and a crowded shared exit the next.
- **Teams.** One account and one IP per person. Claude Enterprise can limit access to allowlisted IP ranges. Your own organisation's admin adds the address; Proxy302 does not register IPs with Anthropic, its IPs are not on any allowlist, and an allowlisted IP does not exempt an account from identity or phone verification.
- **Travel.** Moving between supported countries, keep using your home static IP rather than switching exits in every country. The destination must be on the list too.
- **Claude Code.** It reads the standard proxy variables (`HTTPS_PROXY`) and does not support SOCKS, so use an HTTP proxy.

## 4. Ways of connecting, compared

| Option | Does the address change? | Anyone else behind it? | For a Claude account you stay signed in to |
|---|---|---|---|
| Public shared VPN exit | Often | Many users | No |
| Rotating residential proxy | Per request or every few minutes | Not applicable: the address is meant to change | No; built for scraping |
| Datacenter IP | Fixed for the term | Depends on the provider | Not recommended; sites see a hosting network |
| Ordinary static ISP IP | Fixed for the term | Static IPs of 30 days or longer are dedicated to the buyer | Yes, the budget option |
| ISP IP picked per AI service (AI subscription ISP) | Fixed for the term | Static IPs of 30 days or longer are dedicated to the buyer | Yes; picked for Claude, country checked before delivery |

Whichever you choose, set it in one place only: one browser profile or the system proxy, not both, and never stacked on a VPN or a second proxy.

## 5. Setup: browser, system, Claude Code, iPhone

1. **Check the list.** Open the [supported countries page](https://www.anthropic.com/supported-countries) and confirm the country you are in is on it.
2. **Buy one IP in the country where you are.** Choose HTTP if you will use Claude Code; browser extensions, system proxies and phones usually want HTTP too.
3. **Copy** host, port, username and password from the console.
4. **Use it in one place:** a browser extension, one antidetect-browser profile, or the system proxy.
5. **Check the exit before signing in:**

   ```bash
   curl -sS --max-time 20 -x "http://USER:PASS@HOST:PORT" https://ipinfo.io/json
   ```

   `country` should be where you are and `org` a broadband provider. Replace USER, PASS, HOST and PORT with your own details.
6. **Claude Code:**

   ```bash
   export HTTPS_PROXY="http://USER:PASS@HOST:PORT"
   claude
   # inside, run /status and read the Proxy line
   ```

7. **iPhone:** Settings → Wi-Fi → (i) next to the network → Configure Proxy → Manual; enter server and port, turn on Authentication, enter username and password. It applies to Safari and apps that follow the system proxy.
8. **Keep it.** Renew before the term ends and the address stays the same; auto-renew can be turned on per IP. After expiry the IP is released and a new purchase gets a new address.

## 6. After a restriction

- **Appeal through the official form.** Per the help article "Safeguards warnings and appeals", sign in to claude.ai with the restricted account and fill in the appeal form shown there.
- **A new IP does not lift it.** The penalty is on the account and its use, not on a network address.
- **Do not sign up again from another IP.** That is evading the penalty and makes things worse.
- **Check the first four rows of table 2.** Payment, shared accounts and region have nothing to do with the network.

## 7. FAQ

**Will a residential IP stop my Claude account being banned?** No. Most reasons in table 2 have nothing to do with the IP, and no provider, Proxy302 included, can promise an account is never restricted.

**I am in mainland China. Can I use Claude with a US or Japanese IP?** That use is not permitted. The policy is about where you are, and mainland China is not on the list; an IP does not change that.

**Claude asked me to verify my identity or phone. What now?** Complete it honestly as Claude asks. An IP is not a substitute, and we offer no way around verification.

**Static or rotating IP for Claude?** Static for an account you stay signed in to. Rotating addresses change constantly and suit scraping, not accounts.

**How many Claude accounts per IP?** One person, one account, one IP. Crowding several people's accounts onto one exit makes everything harder to manage and to troubleshoot.

**Does Claude Code work with SOCKS5?** No. It does not support SOCKS; use an HTTP proxy as in section 5.

**Which IP for a Claude Enterprise allowlist?** A static one, so the listed address stays valid. Your own admin adds it in Claude's admin settings; our IPs are not on any allowlist and do not skip identity or phone verification.

**I am travelling to another supported country. Should I switch to a local IP?** No need. Keep your home static IP for the most consistent sign-in history, as long as the destination is on the list.

**Is it the same address after renewal?** Yes if you renew before the term ends. After expiry it is released and a new purchase gets a new address.

**My account is already restricted. Will a clean IP bring it back?** No. Use the appeal in section 6.

## 8. Related guides

- [What IP should I use for Claude and ChatGPT?](https://github.com/proxy302/proxy-guides/blob/main/which-ip-for-claude-and-chatgpt/README.md)
- [What proxy should I use for Claude?](https://github.com/proxy302/proxy-guides/blob/main/proxy-for-claude/README.md)
- [Claude Code proxy settings](https://github.com/proxy302/proxy-guides/blob/main/claude-code-proxy-settings/README.md)

## 9. What Proxy302 sells

- **AI subscription ISP:** native ISP static IPs picked per AI service, 30 days each. Claude tier 15 PTC (for Claude Pro and Max), GPT/Grok tier 10 PTC, Gemini tier 8 PTC; the first IP in each tier is half price (1 PTC = 1 USD).
- **Ordinary static ISP:** $0.50 for one day or $7.99 for 30 days per IP, the same in every country; one day is the cheapest way to test.
- Both are for people in a country the service supports who want one fixed exit for their own account. Prices: [proxy302.com/pricing](https://proxy302.com/pricing/).

## Changelog

- 2026-11-21: first version.

*Facts checked 20 November 2026.*
