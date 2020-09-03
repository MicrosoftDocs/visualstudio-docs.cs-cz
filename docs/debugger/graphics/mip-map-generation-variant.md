---
title: MIP – varianta generace mapování | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 422a68f4e33733aa2874c639f0dcc799cd3ec795
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734893"
---
# <a name="mip-map-generation-variant"></a>Varianta generování mipmap
Povoluje mapy MIP u textur, které nejsou cílem vykreslování.

## <a name="interpretation"></a>Interpretace
Mapy MIP se primárně používají k odstranění artefaktů aliasů v texturách v rámci minifikace, a to tak, že předem vypočítávají menší verze textury. I když tyto další textury spotřebovávají paměť GPU – přibližně 33 procent více než původní textura – jsou taky efektivnější, protože větší část jejich povrchu se vejde do mezipaměti textur GPU a její obsah dosahuje vyššího využití.

Pro trojrozměrné scény doporučujeme mapování MIP, pokud je k dispozici paměť pro uložení dalších textur, protože zvyšují výkon vykreslování i kvalitu obrázku.

Pokud se v této variantě zobrazuje významný nárůst výkonu, znamená to, že používáte textury, aniž byste povolili mapování MIP, a nezískáte tím nejvíc z mezipaměti textury.

## <a name="remarks"></a>Poznámky
MIP – generování mapy je vynucené při každém volání `ID3D11Device::CreateTexture2D` , které vytvoří zdrojovou texturu. Konkrétně generování mapy MIP je vynuceno, když předaný objekt D3D11_TEXTURE2D_DESC v `pDesc` popisuje nezměněný prostředek shaderu; to je:

- Člen BindFlags má pouze nastavený příznak D3D11_BIND_SHADER_RESOURCE.

- Člen použití je nastaven na hodnotu D3D11_USAGE_DEFAULT nebo D3D11_USAGE_IMMUTABLE.

- Člen CPUAccessFlags je nastaven na hodnotu 0 (bez přístupu k procesoru).

- Člen SampleDesc má svůj člen počtu nastavený na hodnotu 1 (žádný vícenásobný ukázkový anti-aliasing).

- Člen MipLevels je nastaven na hodnotu 1 (žádná existující mapa MIP).

  Když aplikace doplní počáteční data, musí mít formát textury automatickou generaci mapy MIP, jak je určeno D3D11_FORMAT_SUPPORT_MIP_AUTOGEN, pokud formát není BC1, BC2 nebo BC3; v opačném případě textura nebude upravena a při zadání počátečních dat nejsou vygenerována žádná mapování MIP.

  Pokud byly pro texturu automaticky generovány mapy MIP, volání `ID3D11Device::CreateShaderResourceView` jsou během přehrávání změněna tak, aby při vzorkování textury používala řetězec MIP.

## <a name="example"></a>Příklad
Variantu **generace v mapě MIP** je možné reprodukovat pomocí kódu takto:

```cpp
D3D11_TEXTURE2D_DESC texture_description;

// ...

texture_description.MipLevels = 0; // generate a full mipchain

std::vector<D3D11_SUBRESOURCE_DATA> initial_data(num_mips);

for (auto&& mip_level : initial_data)
{
    // fill mip_level with the application-supplied initial data
}

d3d_device->CreateTexture2D(&texture_description, initial_data.data(), &texture)
```

Pokud chcete vytvořit texturu s úplným řetězcem MIP, nastavte `D3D11_TEXTURE2D_DESC::MipLevels` na 0. Počet úrovní MIP v úplném řetězci MIP je podlahou (log2 – (n) + 1), kde n je největší rozměr textury.

Pamatujte, že když zadáte počáteční data do `CreateTexture2D` , musíte pro každou úroveň MIP zadat objekt D3D11_SUBRESOURCE_DATA.

> [!NOTE]
> Chcete-li zadat vlastní obsah úrovně MIP namísto automatického generování, je nutné vytvořit textury pomocí editoru obrázků, který podporuje textury mapované na MIP, a poté načíst soubor a předat úrovně MIP do `CreateTexture2D` .

## <a name="see-also"></a>Viz také
[Varianta rozměrů pro polovinu/čtvrtletí](half-quarter-texture-dimensions-variant.md)
