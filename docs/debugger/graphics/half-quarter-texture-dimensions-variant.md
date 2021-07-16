---
title: Half-Quarter varianty dimenzí textury | Microsoft Docs
description: Pokud menší textury ukazují velké zvýšení výkonu, navrhuje zatížení šířky pásma paměti nebo neefektivní použití mezipaměti textur GPU. Zvažte z menší velikosti textury.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ddd446e588af438e1a4d950e9407392e74881f90
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232398"
---
# <a name="halfquarter-texture-dimensions-variant"></a>Varianta polovičních/čtvrtinových dimenzí textury
Zmenšuje rozměry textury u textur, které nevykreslují cíle.

## <a name="interpretation"></a>Interpretace
 Menší textury zabírají méně paměti, a proto spotřebovávají menší šířku pásma paměti a snižují tlak na mezipaměť textur GPU. Nižší podrobnosti ale mohou způsobit snížení kvality obrázku, zejména pokud jsou pečlivě prohlížet ve 3D scéně nebo při zvětšování.

 Pokud tato varianta vykazuje velké zvýšení výkonu, může to znamenat, že vaše aplikace spotřebovává příliš velkou šířku pásma paměti, používá mezipaměť textury neefektivní nebo obojí. Může také značit, že textury zabírají více paměti GPU, než je k dispozici, což způsobuje stránkování textur do systémové paměti.

 Pokud vaše aplikace spotřebovává příliš velkou šířku pásma paměti nebo používá mezipaměť textur neefektivní, zvažte zmenšení velikosti textur, ale až poté, co zvážíte povolení map mip pro vhodné textury. Podobně jako menší textury i textury mapované pomocí mip spotřebovávají menší šířku pásma paměti ( i když zabírají více paměti GPU) a zvyšují využití mezipaměti, ale nesníží detaily textury. Mapy mip doporučujeme vždy, když zvýšené využití paměti nezpůsobí stránkování textur do systémové paměti.

 Pokud textury zabírají více paměti GPU, než je k dispozici, zvažte zmenšení velikosti textur, ale až poté, co zkomprimujte vhodné textury. Podobně jako menší textury zabírá komprimované textury méně paměti a zmenšují potřebu stránkování do systémové paměti, ale jejich barevná věrnost je nižší. Komprese není vhodná pro všechny textury v závislosti na jejich obsahu – například pro ty, které mají významnou variaci barev v malé oblasti – ale u mnoha textur může komprese zachovat lepší celkovou kvalitu obrázku než zmenšení jejich velikosti.

## <a name="remarks"></a>Poznámky
 Při každém volání metody se zmenšuje rozměry `ID3D11Device::CreateTexture2D` textury, které vytvoří zdrojovou texturu. Konkrétně jsou dimenze textury zmenšeny, když D3D11_TEXTURE2D_DESC předaný objekt popisuje texturu, která se používá při `pDesc` vykreslování. To je:

- Člen BindFlags má nastavený pouze D3D11_BIND_SHADER_RESOURCE příznak.

- Člen MiscFlags nemá nastavený příznak D3D11_RESOURCE_MISC_TILE_POOL nebo příznak D3D11_RESOURCE_MISC_TILED (velikost prostředků s dlaždicemi se nezmenšuje).

- Formát textury je podporován jako cíl vykreslení určený D3D11_FORMAT_SUPPORT_RENDER_TARGET, který je nutný ke zmenšení velikosti textury. Podporují se také formáty BC1, BC2 a BC3, i když nejsou podporované jako cíle vykreslování.

  Pokud aplikace dodá počáteční data, tato varianta před vytvořením textury škáluje data textury na odpovídající velikost. Pokud jsou počáteční data dodána ve formátu komprimovaném bloku, jako je BC1, BC2 nebo BC3, před vytvořením menší textury se dekódují, škálují a znovu zakódují. (Povaha komprese založené na bloku znamená, že dodatečný proces kódování dekódování ve škálování téměř vždy způsobí nižší kvalitu obrázku než při generování textury komprimované blokem ze škálované verze textury, která ještě nebyla kódována.)

  Pokud jsou pro texturu povoleny mapy mip, varianta odpovídajícím způsobem snižuje počet úrovní mip – o jednu méně při škálování na polovinu nebo dvě méně při škálování na čtvrtletní velikost.

## <a name="example"></a>Příklad
 Tato varianta mění velikost textur za běhu před voláním `CreateTexture2D` metody . Tento přístup doporučujeme použít pro produkční kód, protože textury v plné velikosti spotřebovávají více místa na disku a protože další krok může zvýšit dobu načítání v aplikaci – zejména u komprimovaných textur, které ke kódování vyžadují významné výpočetní prostředky. Místo toho doporučujeme změnit velikost textur offline pomocí editoru obrázků nebo procesoru obrázků, který je součástí kanálu buildu. Tyto přístupy snižují požadavky na místo na disku a eliminují režijní náklady na běh ve vaší aplikaci a poskytují větší dobu zpracování, abyste si při zmenšování nebo komprimaci textur mohli zachovat nejlepší kvalitu obrázku.

## <a name="see-also"></a>Viz také
- [Varianta generování mipmap](mip-map-generation-variant.md)
- [Varianta komprese textur BC](bc-texture-compression-variant.md)