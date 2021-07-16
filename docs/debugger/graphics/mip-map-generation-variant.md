---
title: Mip-map Generation Variant | Microsoft Docs
description: Pokud generování mip-map vykazuje velké zvýšení výkonu, znamená to, že používáte textury bez povolení map mip a nezískáte z mezipaměti textury nejvíce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e17981b819ccc719399a6ed14071615f2deb54a
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232437"
---
# <a name="mip-map-generation-variant"></a>Varianta generování mipmap
Povolí mapy mip na texturách, které nejsou cílem vykreslení.

## <a name="interpretation"></a>Interpretace
Mapy Mip se primárně používají k eliminaci artefaktů aliasů v texturách pod minifikací díky předběžném výpočtu menších verzí textury. I když tyto další textury spotřebovávají paměť GPU – přibližně o 33 procent více než původní textura – jsou také efektivnější, protože větší plocha jejich povrchu se vejde do mezipaměti textur GPU a její obsah dosahuje vyššího využití.

Pro 3D scény doporučujeme mapy mip, když je k dispozici paměť pro ukládání dalších textur, protože zvyšují výkon vykreslování i kvalitu obrázků.

Pokud tato varianta vykazuje výrazné zvýšení výkonu, znamená to, že používáte textury bez povolení map mip a tím nezískáte z mezipaměti textury nejvíce.

## <a name="remarks"></a>Poznámky
Generování mip-mapy je vynuceno při každém volání metody `ID3D11Device::CreateTexture2D` , které vytvoří zdrojovou texturu. Konkrétně je generování mapy mip vynucené, když D3D11_TEXTURE2D_DESC předaný objekt popisuje neměnný prostředek `pDesc` shaderu, to znamená:

- Člen BindFlags má nastavený pouze D3D11_BIND_SHADER_RESOURCE příznak.

- Člen Využití je nastavený na hodnotu D3D11_USAGE_DEFAULT nebo D3D11_USAGE_IMMUTABLE.

- Člen CPUAccessFlags je nastavený na hodnotu 0 (bez přístupu k procesoru).

- Člen SampleDesc má svého člena Count nastavenou na hodnotu 1 (bez multi sample anti-aliasing (MSAA)).

- Člen MipLevels je nastavený na hodnotu 1 (žádná existující mip-map).

  Pokud aplikace dodá počáteční data, musí formát textury podporovat automatické generování mip-mapy – podle D3D11_FORMAT_SUPPORT_MIP_AUTOGEN – pokud formát není BC1, BC2 nebo BC3. Jinak se textura neupraví a při dodání počátečních dat se nevygenerují žádné mapy mip.

  Pokud byly pro texturu automaticky vygenerovány mapy mip, volání metody se během přehrávání upravují tak, aby při vzorkování textury bylo používání `ID3D11Device::CreateShaderResourceView` řetězce mip-chain.

## <a name="example"></a>Příklad
Variantu **generování Mip-map** je možné reprodukovat pomocí kódu, jako je tento:

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

Pokud chcete vytvořit texturu, která má úplný řetěz mip, nastavte `D3D11_TEXTURE2D_DESC::MipLevels` na 0. Počet úrovní mip v plném řetězu mip je floor(log2(n) + 1), kde n je největší rozměr textury.

Nezapomeňte, že při poskytování počátečních dat do souboru musíte `CreateTexture2D` zadat D3D11_SUBRESOURCE_DATA pro každou úroveň mip.

> [!NOTE]
> Pokud chcete místo jejich generovat automaticky zadat vlastní obsah na úrovni mip, musíte vytvořit textury pomocí editoru obrázků, který podporuje textury mapované na mip, a pak soubor načíst a předat úrovně mip do `CreateTexture2D` .

## <a name="see-also"></a>Viz také
[Varianta polovičních/čtvrtinových dimenzí textury](half-quarter-texture-dimensions-variant.md)
