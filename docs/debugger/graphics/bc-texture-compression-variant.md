---
title: Varianta komprese textur BC | Microsoft Docs
description: Pomocí varianty komprese textury BC povolte kompresi bloků (BC) na texturách ve formátu pixelů, který je variací B8G8R8X8, B8G8R8A8 nebo R8G8B8A8.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1a8699980599a590b6f6e58e14ea504f52db609
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232749"
---
# <a name="bc-texture-compression-variant"></a>Varianta komprese textur BC
Umožňuje kompresi bloků u textur ve formátu pixelů, který je variací B8G8R8X8, B8G8R8A8 nebo R8G8B8A8.

## <a name="interpretation"></a>Interpretace
 Formáty komprese založené na bloku, jako jsou BC1, BC2 a BC3, zabírají výrazně méně paměti než nekomprimované formáty obrázků, a proto spotřebovávají výrazně menší šířku pásma paměti. V porovnání s nekomprimovaný formát, který používá 32 bitů na pixel, dosahuje BC1 (dříve DXT1) komprese 8:1 a BC3 (dříve DXT5) dosahuje 4:1. Rozdíl mezi BC1 a BC3 spočívá v tom, že BC1 nepodporuje alfa kanál, zatímco BC3 podporuje kanál alfa komprimovaný blokem. I přes vysoké kompresní poměry je u obvyklých textur pouze menší snížení kvality obrázku. Komprese bloků určitých druhů textur – například těch, které mají významnou variaci barev v malé oblasti – ale může mít nepřijatelné výsledky.

 Pokud jsou textury vhodné pro kompresi založenou na bloku a nepotřebují dokonalou věrnost barev, zvažte použití formátu komprimovaného do bloků, abyste snížili využití paměti a spotřebovávají menší šířku pásma.

## <a name="remarks"></a>Poznámky
 Textury se komprimují pomocí kompresního formátu založeného na bloku při každém volání metody `ID3DDevice::CreateTexture2D` , která vytvoří zdrojovou texturu. Konkrétně jsou textury komprimovány v případě, že:

- Objekt `D3D11_TEXTURE2D_DESC` předaný `pDesc` v popisuje neměnný prostředek shaderu, to znamená:

  - Člen BindFlags má nastavený pouze D3D11_BIND_SHADER_RESOURCE příznak.

  - Člen Využití je nastavený na hodnotu D3D11_USAGE_DEFAULT nebo D3D11_USAGE_IMMUTABLE.

  - Člen CPUAccessFlags je nastavený na hodnotu 0 (bez přístupu k procesoru).

  - Člen SamplerDesc má svého člena Count nastavenou na hodnotu 1 (bez multi sample anti-aliasing (MSAA)).

- Počáteční data jsou k dispozici pro volání `CreateTexture2D` .

  Tady jsou podporované zdrojové formáty a jejich formáty komprimované do bloků.

|Původní formát (z)|Komprimovaný formát (do)|
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

 Pokud má textura formát, který tu není uvedený, textura se neupraví.

## <a name="restrictions-and-limitations"></a>Omezení a limity
 V některých případech textury vytvořené s variací formátů obrázků B8G8R8A8 nebo R8G8B8A8 ve skutečnosti alfa kanál nevyužít, ale neexistuje způsob, jak variantu použít. Aby byla zachována správnost v případě použití alfa kanálu, varianta vždy tyto formáty zakóduje do méně efektivního formátu BC3. S touto variantou můžete lépe porozumět potenciálnímu výkonu vykreslování vaší aplikace, a Analýza grafických snímků použít variantu formátu obrázku B8G8R8X8, pokud kanál alfa nepou3/4íte, aby varianta mohl využívat efektivnější formát BC1.

## <a name="example"></a>Příklad
 Tento variantní blok komprimuje textury za běhu před voláním `CreateTexture2D` metody . Vzhledem k tomu, že nekomprimované textury spotřebovávají více místa na disku a další krok může výrazně zvýšit dobu načítání v aplikaci, protože komprese založená na bloku vyžaduje ke kódování významné výpočetní prostředky. Místo toho doporučujeme komprimovat textury offline pomocí editoru obrázků nebo procesoru obrázků, který je součástí kanálu buildu. Tyto přístupy snižují požadavky na místo na disku, eliminují režii za běhu ve vaší aplikaci a poskytují větší dobu zpracování, abyste mohli zachovat nejlepší kvalitu image.

## <a name="see-also"></a>Viz také
- [Varianta polovičních/čtvrtinových dimenzí textury](half-quarter-texture-dimensions-variant.md)