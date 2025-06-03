<script lang="ts">
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';


  import { cn } from '$lib/utils';
  import { AlignJustify, XIcon } from 'lucide-svelte';
  import { fly, fade } from 'svelte/transition';

  const menuItem = [
    { id: 'motivation', label: 'Motivation', href: '/' },
    { id: 'callForPapers', label: 'Call For Papers', href: '/' },
    { id: 'organizers', label: 'Organizers', href: '/' },
    { id: 'comittee', label: 'TPCMs', href: '/' },
    { id: 'speakers', label: 'Speakers', href: '/' },
    { id: 'developers', label: 'Developers', href: '/' },
  ];

  let hamburgerMenuIsOpen = false;

  function toggleOverflowHidden(node: HTMLElement) {
    node.addEventListener('click', () => {
      hamburgerMenuIsOpen = !hamburgerMenuIsOpen;
      updateOverflowHidden();
    });
  }

  function updateOverflowHidden() {
    const html = document.querySelector('html');
    if (html) {
      html.classList.toggle('overflow-hidden', hamburgerMenuIsOpen);
    }
  }

  

  function scrollToSection(event: Event, id: string) {
		event.preventDefault();
		if (window.location.pathname === '/') {
			const target = document.getElementById(id);
			if (target) {
				const targetPosition = target.getBoundingClientRect().top + window.scrollY - 100;
				window.scrollTo({
					top: targetPosition,
					behavior: 'smooth'
				});
			}
		} else {
			goto('/').then(() => {
				const target = document.getElementById(id);
				if (target) {
					const targetPosition = target.getBoundingClientRect().top + window.scrollY;

					window.scrollTo({
						top: targetPosition,
						behavior: 'smooth'
					});
				}
			});
		}
	}

	

	function handleLinkClick() {
		hamburgerMenuIsOpen = false;
	}


 onMount(() => {
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', (e: Event) => {
        e.preventDefault();
        const target = e.currentTarget as HTMLAnchorElement;
        const href = target.getAttribute('href');
        if (href) {
          const el = document.querySelector(href);
          if (el) {
            el.scrollIntoView({
              behavior: 'smooth'
            });
          }
        }
      });
    });
  });
  let innerWidth = 0;
</script>

<svelte:window bind:innerWidth />

<header class="fixed left-0 top-0 z-50 w-full -translate-y-4 animate-fade-in border-b opacity-0 backdrop-blur-md">
  <div class="container flex h-14 items-center justify-between">
    <!-- <a class="text-md font-extrabold flex items-center" href="/">QNLP</a> -->
     <a href="/" on:click={(event) => {
                  event.preventDefault();
                  handleLinkClick();
                  scrollToSection(event, 'hero');
                }} class="flex items-center gap-2">
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="72" height="35" viewBox="0 0 252 121">
          <image xlink:href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAPwAAAB5CAYAAAAd1kwMAAAAAXNSR0IArs4c6QAAGhVJREFUeF7tXYt2U7cSzbENKy2vlJA25VECpV38ReFLWr6E9Eua+yXX/AOr0NWWOg0PQwgEQoC2jn29T4985WNJM3oeJ1HWuqvttY5GM9LWPDQaFQvz+7dWDQ3/xP+u1v4b/3mr+v96NTbw3+L/u1f9e3d+Wc0jyxJII4EiDRk2FQD7+wrIAszsjxkNsQkA+HkTYAgrNzl6Emga8EJ7fzcW7XoD4sUGsFFtANkCaGACMsm0EmgK8HcjanFXCQrw/+jaQf4uS2DeJZAa8AB6E5rcZh4y8G2kldseKgmkAjyA/kMVfDssAsrAPywzlcfJlkBswCPw9tMhA/pEeEVRLIxGowx89nLKDeddArEAj2AcgB400l4BcMH0z4gC77VarR8PDg4Q5Mt/WQKHUgIxAN+Yn55iQxiNRohB5MDeoVzuedAhAU9q9dSaOSK93nA4vC0l9+SVlCVwKCQQCvAA+38pXz0iAJXCjkwvg/5QLPE8SFkCIQB/qygKgN36LzIgZ8YTgV5vNBptDIfDbOJbz37+oAkJ+AL+7hhEwc7VIwDSSqau9OHXZ9BbiTo3bkgCzoCHVi+K4tZ4sZdR8xh/rgD0HYtL8A/HdwcHB9d8aefvswRiSsAJqZUJD1Me59QZ8P+foe5gMEAwL/9lCcylBKwB32q1SjNeAF33zxjcptb4HHr1DQ/m/WAwyD59jAWQ+/SWgBXgO53OreFwSAboXExib07Gh+McgIagI/rQ0Rv/nkEfUtC5r2ASYAMeYB+NRiTY5ZFxgH+UXAKJXxzZ3RkMBvnKbbClmjsKIQEu4Nfa7fYftgQ5GveIAh6iQiru7Y8fP9ar8diKMbfPEggmARbgO50ONLt3XjxnAwjGmaKj1PSLouj99ddfOXIfc1Jz31YSIAHfbrejH79RPvEhP/bb+Pvvv+9YzUpunCUQSQJGwJ84ceKH0Wj0k0ozRhrPVLcNaOTJMWP99MGH36IoYNpnf95HiPnbIBIwAl6Y8hnwpCFETUY27SkJ5d+TSEC7kqHdqzvtk4Gk1rh1CaSmH5jenY8fP+a79EmWdSaik4AJ8IjKi9rwLAkGBgiLptwoNX1Ler2PHz+yA3iLi4uQPWoLOP+1Wq2F4XC4UPsnxuGVGLS4uHir1WqhnLjz3/v3741xDfDfbrfv+iR2HRwc/JjilOTUqVNQjqi8PPWnkX85HzZ/SNsuimIT3+DfO51Ob3d31+n0Rwn4kydPBiliYQkIjgzKBybGOfzdaiGL+vLiBOG78e21tYruVOpvSJ9cu3tKqcYqeqPRiK3lASrqFiJHvqpjT9zl94kpYIHrYjvcY9b9/X2jn3T69OmZvA8Ov/LcDAaDaykAf+bMmSCnWJYWbVl6bTyX9969e8eOD+kAP+Kgj2pjO0Ga/gDwDVutVGnI75HqGjvnX4ybwW/vw4cPLC0fCvAqmY5Go+6HDx+cc/4z4Kel2hDg5UGU4H/79i1puc0A/uTJk4jKw0QJ/scAxAwTtkCvD1oAH1VzxxvHGlcDhWBeE+xcf//+PTkxldkcLLNR5gdmYavVumOjGeTvKxMWNQun/mzm9927d6SGr4qqaKeCotdut6+5mr428y8AH1uxUPxW1u+d3d1drcafEjrAMRwO/0gVlTcwsO4LdAPwJ/f3GQK0mXeybUWPpeVdAE8NoMbvBuVH6/rTAd5mAwgBeIrfTqfTGOBTupCyhQnQoyiLTtvXAf/TePefaPeGAMH2c6kJV/2+uLioLdqRkF9Sy6t8WBd+Dd/09vf3We5FvQ8AviiKGQ1PjU+W797eHqnhqRgGRS+Vhj937tx/x27STCZqwvVUiqJGr/fmzZuZ+a0D/g8EveQdwydKSk2I4nevYBKX3uLionLBppogBB339/eNPnRMwEt8ro81LeleZMCbV9acAh4bwMbu7u7UaUgd8MZgXUxAjEajJGAXUwf3ZXy0pLwQZOIzUAyA1K4APHzYQPSUKxa5/nt7e9Za/syZMzM5GtzNVrTjaPhWq2UVw6iPodVqJTHpAXjOXZOY+DHIf313d3eyqU8AD61XT7SxnURXhlKDXfAlos22fIawgJBuawqahTiW4vCFo8L9/X2rhCAAvn4sx6Elt+EC3sfCnDfAUzJyxQ/V7/h15NsikCcDvrwkw/iY3YTDgO8REXswmoanTp1i7c6qzwV/jhtA9927d1qzXmh4E38c+TLkY63lhYb3Ce6Og0pGH35paWmm2Iotv0VRJNHwS0tLzmsowfyCRO/169elJTcR+ieffBLk7L3s1JCAUjdRh8NhkuQInWCrjC7ru/5cPnUmOY7GTEGzhIBH9pbR2qjLLgN+WiKHAPDlHEPLl4D3NW11YKKAjwIRrmfBDM3FbuIada4ToPjF7/KfCWgAvG2U2lYDirHAytrb22Mn4gDwiNK70gPdN2/ekBqeqrDEoJ9Uw8/BObx2zWOOX79+fbsU+qeffloexzEEyAYR1ZATqab6CPn76dOnS7MscpBs6vrtePzaKLkL4G02oHpbpNtyN18BeEr+pvUUAvAMfhsDfFPn8KaYB+ZYAH7qooytpqImXvO7dbDIkQ7rM2GmKqrQxizD3Xv79q0ySg7A+0apGYCQNyAka7AKdSwtLZVBO5ZgpUbyuhpHjkkNT2XaMegnAfxnn32m9OEtFOjU60XtdruMpY1GI9xpYV9go3ALi7qQj6eoD+omKUPg2ibU5Qmfvl2+hRxOnDiBPIRoAFcBUBe8Sg34Ki0Tfh55CysDfnomAwB+/dWrVzP5EEtLSzg6xq1E1utOFH7RT2FK8LDYoawwhoSAvb09ljax6tizsSonOvYGoDs6QpQaPmxM+or5nUnUUIkUgPc9wuVoeNsYRn2so9EoiYZfXl5WZtpxLSwAUQV48f3y8rKTvBXzu15w86JVE8/ZEFQL1uXs1xPLrM8pv5nDL4uQ1EjnO4c4lrIdC7S8Kh2z3k9KwPucw6cCPDS855G2EfDQ9O12Gy6U17E54mYl4F3yol03AHxHJV04LNQgn0CwuDzE7SzEBoAEHNXtJqHhbeUcwCLAbStjIo4AvM85/OvXr0kfvq7hbeWNI1+Oi8Kdb107aHgfMI75Wn/58qUxxfnChQveQWVkVsKkD1LsAsLgTAiOB0wJJ77C9/0eZj13t+bwS41nXMlECbBAgMc1SVutgGoqxnTbDPjpWU0B+OXl5fLauueG3i3OnDkDUyHl/fe59N/FFHLzom01rwH4U7nOoh0Abxulrm9ASKlEH7bBVpGkYdBoPwyHQ69z+LHPatTwFy5cIJ81ozZcvOabQsML7Utt7qY1wNHw8mvNjsd+GxPAO3bgwuNcA/7s2bPBCoCIBSmEpDGBlYEyF8ArJgOaGvxM8guYx45lkoZucqHhOW6gCZAU4MG/7bFknV4qkx6Ax/VYagPyBPxMJqwDvRLwkzN4hw5cAL/OKcXj0nGIb5aWloK5ONR4Knl3d3d3Z8CFBe8bpYafLIPTZn4RTNRVTkHU2Pccfmdnh9TwVKYdJd+mNDx1PFa3uFCGzaThV1ZWWFY4Nb8IlicHPIju7e1Z3c6iJjbk7yEi0NzxJAI8inqWgUhqQcjjFqmYKl4y4KelUjfpQwF+dXV17eDggB2dp+a3BPzZs2e1l2aoDrgLW26ni0q79BXjG6FZE7o4k5tMMj/CpPUJ0giz+fz580oNQSzMsu7dy5cvZ+qjuZ4Ly67NWKORGt42hlFfDyhx1e/3yUQi33W0srLinGlXze/GOG6CCszYlK8iu66qvmwbcJ1ipT6/yPkwAp4ShMuGcAgAr01ycOGXkqF8dbEOeN9jKQH4KmOLfdwoAXNjZ2dnJkHKF/Don2PSywVAXDZglKlOEbTTAZ6ae44l4LPh1+hvvHjx4k5x7tw56wcndIwwAaGMSlPCSfU7fHici3LoMfk1dqUznUNEqWVQOR4d9XZ2dmaO6ATgZf458pLbcDQ8Njxd4g1nA0BNu1QannuUa5ITZwOwlbO0ed/u9/tdAN4raaBmrnMeY5xrwMP8lQt5uk6QxcRsvHr1akaLmgDPXRgy4NGfYxDszs7OzlTMZR4AL+Rr0oBHCfAW60nVtPv8+fMyMIwobjDA1ylpFqYyKu3JULDPdf4uh4CjxleazRyAUvTqWtTlvBjZWdvb21NafmVlxfvlme3tbdKH93Vp4LOm0PBffPFFFAxR88tZk1WbO/1+v9y0AfgyoMMxkSwImJrONeAD5EVreddMoDKPmgN4aj7qfrKsmalva7/floN3AvDMDX7qdEB84wJ4asx1+abS8AB8/RyeGmuI35kbQrff70+OfQH4ybkzswPfsSqj0r6dhvr+/PnzeIiDfQfZhq5GvjMmM/oE4H2j1HUNXx3zQBtNXuBhBoWmtDwAz7ktZ1pPL168IDW8beJNfS5Sa/hE+LFRKN1nz55N5XiUiRli8lINmErdtAFRyLbCb64nRoSi0TTgwYcAq61FhzkTWj4DfnpFrK6u+mbaOS0xsZ7Ex7X11ev3+7MPUZgyuiJuAMbrgE7cB/gIFxSqN+hmgo8Bup/pAvL9559/lEdH2Hx8M+1UZnOl5Z0Scba3t0ttAcBzUmtNJv/z58+NGn51ddU1yDghi6q1KXx4AF51SSkifpTLUdoA8NwU/PaZHApoeOeF5cFQ79WrV9YPIMQAndzn8vKy8YjSg1/t0HVnxQLwPvfBdX6ya6qm0PKugJeFQJn0AvBMl0MHgEYBT63XGOsJabr9fl971RaA177AQg3YtINTJiMScFRZXLY0Q7VHQMtWa4WYMB0oVRrelp4OVNDyNvf+JRmXyRurq6szt+Vs54Gj4X0TbxYWFpIA/ssvvwwSpbed35rMy8zIx48fG9+KL82qUJFpywErj6NsF06o9uK+sU1/lvyqut7Y3t5WlvqKCfjKLGff+5d8xN7z58+vZcBPT2WTgEfiFirZPH36lPVGYAn48+fPs7PLQgECDzEcHBywiiba0HRtu7Ky4v0Qh+0GAD9re3tbeZEIgKei1BQ9kxZ18ZGrYCayEDfrT03Zmt5js5P04eunFBS/9blHiasUPjwAHyLTjrKYkYaNNsiNANC5IJf7LYUuR6dtJ84GYPUJGx8PzYWWd82FpninFqjp2IgDeB19QZfykx0TRnpFUfyouh5L8SuP1wXwFCAU6ysZ4BG0k+lTa6P2O8pU/6fT6SwMBoMF/FP+GwwGiLgHuQRUAr4qkofzZ05qrCUv+uYVvUZ9eQEsKuYQgum6fE2AdNHA9TEy/ORJxpwlf6zSWab19OzZM1LD255S1Oml0vCXLl3yOpZDoM1FW1vOWdl8IvR6kbxUAICZUk/ddGHE9RuY8qqF6dqf6bsanTIApmufCPBIMCoTcRLwO5VxlwH/f4k3BXhWxl0kk18bvIqxEEWfqpRIZgko72GheKXIb1Z1BsD7ZtpRZjPoIgBnezrhyry84Y01GqnhqRgGNQ6UuAplCptoQcPL5/Amy0aDn/XHjx+zgm4Uz9TvE6HDrO90OlZ3pkO6AFSZH4oR29/ht1OBFs7EuW6ADHO7BLzPOTwT8NDuZCKOK5+6eeFoeADeh25TgOeuRWl9pQc8BmkbvJIye/71DzxjADheENf4uEJzaecYrLJ6BpsY10a/3ze+vKPS8LbypUAlxnjx4kXllWBbejZzQWn4y5cvT7284+JiItcDAS+bcenamiyFy5cvO53DS/hpDPCsYnlCKJwF4bBDI4EAl/WDTJQ8gUg4qaLLTqWDOPwyF5fRnK9M7RmT3pY+F/CQi6h7J4/flh6T97JZCsDbjIdSWMiI1K3JQwt4jwysIBpemiCcMyKoFcyvWV1dDV6N1hUQHCBCw1NRaoo+BSoZEJyzZIqeDcCePHli9OGh4U0ujYvGtxlffQPAVdter6dUQleuXHHS8JLiXP/zzz+DrXUTnzNCR541XriwFQ6nvcOC8QI+NrCxf1q+vpligdRloOGX1O5Cw1OAp+hxNhbRBzYY3yCZzfxyAE9V6LGhx1mfpjYcDe96Dj/+rjnAV2avVfDOVZgWE4adFRlpmzjGU90CqkAijpegHVD9c6o2nQU9V5ao73rPnj1jXRoKAUAbDY+B16PNFDO63znBznFUmqXhbcYQc345Gl4FeKZL2xzgIeDPP/88mpaXJ9BzgoR5hSQQAJ30yz3p2aw9ZVtcbnjy5AmrJn9DgGcVtvABuvj2uACeuWiaBbzQ8q4mCpPJmWapAZmYXu/p06cs7Q7BiCi1qyzxHWU21/vGvNsezRr9RcOpzdbWFqnhbV0aysXxWc9Ig9b58FevXvXOtGvMhxdCU2n5xAA5UhsCnm7SuSIq0IQ4lrIFfLXRlMHN2DEPjoaXy1T7bHwuFkn9Gw7gqTHq8AN5Nw74KuBl9OWb2gA4PiIlfJffPfjtPnnyRPs4ow7wnMQbk49IgUpFV9byHvyS4uVoeN/EG3IQtQYmflE9x6ThOS6lwQJZ7/V6zUTp5UFRR1kxF4RqspoCuhiLK79IAKEKE9T5pY6lOIvZBfDo98qVK2Uijiu/nLFlwE8lqs0N4JGQEewxO85CsGkTc0FyxsGk75RFJQAvj4NJb/IJBSodj2tra3jEcMa6s6VvkuHYhDX68Gtra96Zdpw55CoWVM/Rafi1tTWvc3iY9HOh4SGMKgvL6UYVRyMzjy2c5i7kAuUMQEGv+/jxYytTXtBRAZ4aQ52+q4avtDy5iH3kywH8cDjEGLR/PvQpWSrM7+MB+Ar03kkZ6IezAdhOhE37xAukt7W1xY7Kq0x63yi1q4bHWLDh2Cbi2Mh3c3OTpeE5gBdtbOjbrJuqLQl413N4XBybGw0vBHPx4kXv1NTIE0LOYWL61n67zAAA5wp4wacP4DEWcdxECrZqYCPfkIBPpEiOF+Axp5cuXbK6XEMtFJsFQvXl8nss+ijnbBukU2l4Ww1b74MymymZra2tlRVxqHa6303yHWs0UsP71gMIOb+onqPz4a9du1a6Px701h89etR8lL4+kfDn2+12GcSLfU5LuQCui9DmO5cJhHmWqpiBDS+5bZZAiSlbMVSgJwsm2PbLae8CQE6/lIbi+oioJLq1teUUpPMZZ/42S4ArAWvAo+MK9KgYM/Mo4RGPumuLfOI679bWlrGoBXdScrssgVgScAK8AP2JEyfuIkGDqwFDM9GUxq/THfOVLDUytAxzf8dLAs6Ah5iQoDEYDMr75iqxpQYkZ+MJaYHgQQAUo+z1esbnfY7XksrczrMEvAAvGPvqq6+g6ZWgl5lPvQFw6HlsABns87yy89iUEggCeKHtVemY8w54x3XR3dzczME5R+Hlz5qTQDDAS6BH8QyyGAXaczRwSNEEopcsKyok77mvLIESczHEcOXKFdy0Qmae14smgQDKZpGgB5flP7rkCzaR3DBLoEEJRAG80PZVgo438DnBuIgyREAOgbngZbMjjjl3nSUQ14fXyReR/OFw+H1VCfcwaXwAPEfgM3COlASiafi6lAB8UTI6lAQjmfwoje0NdPDbarXuPnr0KCfjhJrw3I+3BJIBXoy0Aj6Ceji/ZwX3bLl0uD1V1r8P4aNXQP8ex5QYB2rZ5XN62xnM7WNJIDngZUZQ1WR8CxNRfS9TXyccAvg4R98YA/KeLyAFyKsgZT3zsPfo0SPne/GxJj73ezwlkBzwkmmP64STW3cxxE8BHo9a4AFLgB7/bhOYEyCveFBaKoI+3sr77bffcjZejEnOfVpJIBngZVO3qag75fOP7wVgA0CwbhKRx/+H8VZWiPyyjY2ge7///nvW8jYSy22jSCA64IVGH4ONTL2tc0gBNLREYtJD5dqs5UPPWO7PVgJRAX/9+nXvslgyQzEBqRJcSHqwFLKWt12euX1oCUQBPLQ6yltzU2y5TIUEIIdmBHpZy3MEn9tEk0BwwEOru5jvNhw6HLvZdK9tG2AD6P7666/50k2Q2ciduEggKOCvX78+VeQyAECseEpNzyXmgAKX2Ze3mtbcOKAEggH+66+/jvpwgQvPTW0AhAWStbzLZOZvgkggCOB1YBcLX4w0NQDniZ5caAPZd1nLB1m/uRNLCXgD/saNG6Rm5wDeo/IMm+U52gC6v/zyS/bl2TOXG4aSgBfgEY3vdDrGJ6VdBpoamJwNyYUP0zfIvnv48GHOvgst2NyfUQJegEfP33zzDXLHnV8nMY2uKeAn2gCyls/gTC4Bb8BjxDdu3IhyFHfEAY903azlky/5400wCOAhwm+//bbMqovpix/BDaD78OHD7Msfbwwm5T4Y4G/evLl2cHBQvjunAmYKrlJvCAHo4WIOtHwun5VigWQaYYtYAvTD4RBR+/JWWQBAeE1Ravq29JCEkwN3XlOcP7aUQDANL+hWoG/ksUlOsG1eXA5UxHn48GGSJ4It10RufoQlEBzwkNXNmzdR2AKafurPQgMKE1c2dcVddHZ1HA69JjaAsdvTffDgQfbdjzCw5pW1KIAXQTzmJRpRdAJn0vc4Ji6siEqgqDTzXVUbj70R1C0BjmUQcAJ7Dx48yMUwAgo0d8WXQDTAV5redB8e2nsjlFmLTQBVYuXXbPli+Ldlglt46z///HM2420nJrcPJoHYgIfWLSP30oiDAr0uiUr7O9XB57gAjpLvtVqtO/fv38+ZdY4CzJ+FkUBUwFdaHsUwysh9ykBVpfERSwD4ncphh9gAUOkGl2Xy0VuYBZt78ZNAdMAL0APwHP/cjx311xX4te/Yu9IkXIDSkskmvKt083cxJJAE8DEG7tKnBHw8dmkd5KNoVhtAWe/+/v372VenBJZ/Ty6BYwV4IV1h7hdFEfL1my5q3GegJ1/DmaCFBI4l4GX5APydTgcZgojy44kokSWotADgk7daLTwhBYDDbL+Xg3EWKy43bVQCxx7wlPSxIeSAGyWl/PthkcD/ALi78cP3ZJ0rAAAAAElFTkSuQmCC" x="0" y="0" width="252" height="121"/>
        </svg>
      </a>

    <!-- Desktop nav -->
    {#if innerWidth >= 768}
      <nav>
        <ul class="flex space-x-6 uppercase">
          {#each menuItem as item}
            <li>
              <a 
                href="/"
                on:click={(event) => {
                  event.preventDefault();
                  handleLinkClick();
                  scrollToSection(event, item.id);
                }}
              >
                {item.label}
              </a>
            </li>
          {/each}
        </ul>
      </nav>
    {/if}

    <!-- Mobile toggle -->
    <button class="md:hidden z-50 relative" use:toggleOverflowHidden>
      <span class="sr-only">Toggle menu</span>
      {#if hamburgerMenuIsOpen}
        <XIcon strokeWidth={1.4} class="text-gray-300" />
      {:else}
        <AlignJustify  strokeWidth={1.4} class="text-gray-300" />
      {/if}
    </button>
  </div>
</header>

<!-- Mobile nav overlay -->
<nav
  class={cn(
    `fixed left-0 top-0 z-40 h-screen w-full overflow-auto bg-background/70 backdrop-blur-md`,
    {
      'pointer-events-none opacity-0': !hamburgerMenuIsOpen,
      'pointer-events-auto opacity-100': hamburgerMenuIsOpen
    }
  )}
  transition:fade
>
  {#if hamburgerMenuIsOpen}
    <ul in:fly={{ y: -30, duration: 400 }} class="flex flex-col uppercase space-y-4 pt-16 pl-6">
      {#each menuItem as item}
        <li>
          <a 
            class="text-xl hover:text-gray-700 transition-colors" 
            href="/"
            on:click={(event) => {
              hamburgerMenuIsOpen = false;
              updateOverflowHidden();
              event.preventDefault();
              handleLinkClick();
              scrollToSection(event, item.id);
            }}
          >
            {item.label}
          </a>
        </li>
      {/each}
    </ul>
  {/if}
</nav>
