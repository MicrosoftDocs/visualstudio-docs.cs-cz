---
title: Varianta komprese textury BC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5faf19632d746105deed3a36af6943627594175
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736165"
---
# <a name="bc-texture-compression-variant"></a>Varianta komprese textur BC
Povoluje kompresi bloků na texturách, které mají formát pixel, který je variantou B8G8R8X8, B8G8R8A8 nebo R8G8B8A8.

## <a name="interpretation"></a>Výsledků
 Formáty komprese založené na bloku, jako je BC1, BC2 a BC3, zabírají podstatně menší velikost paměti než u nekomprimovaných formátů obrázků, a proto spotřebovávají výrazně menší šířku pásma paměti. V porovnání s nekomprimovaným formátem, který používá 32 bitů na pixel, BC1 (dříve označované jako DXT1) dosahuje 8:1 komprese a BC3 (dříve označované jako DXT5) dosahují 4:1. Rozdíl mezi BC1 a BC3 je, že BC1 nepodporuje alfa kanál, zatímco BC3 podporuje komprimovaný kanál alfa. Navzdory vysokým kompresním poměrům je u typických textur jen menší snížení kvality obrazu. Nicméně zablokovat kompresi určitých druhů textur – například ty, které mají významnou variaci barev v malé oblasti – mohou mít nepřijatelné výsledky.

 Pokud jsou textury vhodné pro kompresi založenou na blocích a nepotřebují dokonalou barevnou věrnost, zvažte použití formátu zkomprimovaného blokem ke snížení využití paměti a využití menší šířky pásma.

## <a name="remarks"></a>Poznámky
 Rozkomprimujete textury pomocí formátu komprese založeného na bloku při každém volání `ID3DDevice::CreateTexture2D`, které vytvoří zdrojovou texturu. Konkrétně jsou textury komprimovány v těchto případech:

- Objekt `D3D11_TEXTURE2D_DESC` předaný v `pDesc` popisuje nezměněný prostředek shaderu; To je:

  - Člen BindFlags má pouze nastavený příznak D3D11_BIND_SHADER_RESOURCE.

  - Člen použití je nastaven na hodnotu D3D11_USAGE_DEFAULT nebo D3D11_USAGE_IMMUTABLE.

  - Člen CPUAccessFlags je nastaven na hodnotu 0 (bez přístupu k procesoru).

  - Člen SamplerDesc má svůj člen počtu nastavený na hodnotu 1 (žádný vícenásobný ukázkový anti-aliasing).

- K volání `CreateTexture2D` je k dispozici počáteční data.

  Tady jsou podporované zdrojové formáty a jejich formáty komprimované z bloku.

|Původní formát (od)|Komprimovaný formát (do)|
|------------------------------|------------------------------|
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (dříve DXT1)|
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (dříve DXT5)|
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|

 Pokud vaše textura má formát, který není uveden, textura se neupraví.

## <a name="restrictions-and-limitations"></a>Omezení a omezení
 Někdy textury, které jsou vytvořeny pomocí variace formátů obrázků B8G8R8A8 nebo R8G8B8A8, ve skutečnosti nepoužívají alfa kanál, ale neexistuje žádný způsob, jak variantu zjistit, zda se používá nebo ne. Aby se zachovala správná velikost pro případ, že se používá alfa kanál, tato varianta tyto formáty vždy zakóduje do méně efektivního formátu BC3. Můžete pomoci Analýza grafických snímků lépe porozumět možnému výkonu vykreslování vaší aplikace pomocí této varianty pomocí variace formátu obrázku B8G8R8X8, pokud nepoužíváte kanál alfa, aby varianta mohla používat efektivnější formát BC1.

## <a name="example"></a>Příklad
 Tento blok varianty – před voláním `CreateTexture2D` komprimuje textury v době běhu. Doporučujeme před tímto přístupem k produkčnímu kódu, protože nekomprimované textury spotřebovávají více místa na disku a protože další krok může významně zvýšit dobu načítání v aplikaci, protože komprese na základě bloků vyžaduje významné výpočetní prostředky ke kódování. Místo toho doporučujeme komprimovat textury offline pomocí editoru obrázků nebo procesoru obrázků, který je součástí vašeho kanálu sestavení. Tyto přístupy omezují požadavky na místo na disku, eliminují režijní náklady za běhu ve vaší aplikaci a poskytují větší dobu zpracování, abyste mohli zachovat nejlepší kvalitu obrazu.

## <a name="see-also"></a>Viz také:
- [Varianta polovičních/čtvrtinových dimenzí textury](half-quarter-texture-dimensions-variant.md)