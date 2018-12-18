---
title: Varianta generování Mipmap | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06b2d1e537152020b42fdff38fab1200b9cf7668
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908532"
---
# <a name="mip-map-generation-variant"></a>Varianta generování mipmap
Umožňuje mapy mip na textury, které nejsou cíle vykreslování.  
  
## <a name="interpretation"></a>interpretace  
 Mapy MIP primárně používají k odstranění třepící artefakty v textury v rámci připravenost k minifikaci předem výpočtu menší verze textury. I když tyto další textury využívat paměť GPU – přibližně o 33 procent větší než původní textura – navíc mnohem efektivnější, protože více z jejich plochy vejde se do mezipaměti textur GPU a její obsah dosáhnout vyšší využití.  
  
 Pro 3D scénách doporučujeme mapy mip paměti je k dispozici pro uložení Další textury, protože zvyšují rychlost vykreslování a kvality obrázku.  
  
 Pokud se zobrazí tato varianta zvýšení výkonu, znamená to, že používáte textury bez povolení mapy mip a tím nedokáže získat maximum z mezipaměti textur.  
  
## <a name="remarks"></a>Poznámky  
 Generování Mipmap je vynucena všechna volání `ID3D11Device::CreateTexture2D` , který vytváří zdrojovou texturu. Konkrétně je nucen generování Mipmap, když D3D11_TEXTURE2D_DESC objekt předaný v `pDesc` popisuje neměnné prostředek shaderu; který je:  
  
- Člen BindFlags má pouze D3D11_BIND_SHADER_RESOURCE příznak nastaven.  
  
- Využití člen je nastavený na D3D11_USAGE_DEFAULT nebo D3D11_USAGE_IMMUTABLE.  
  
- Člen CPUAccessFlags je nastavený na hodnotu 0 (žádný přístup procesoru).  
  
- Člen SampleDesc má jeho Count – člen nastavena na hodnotu 1 (žádné více ukázka Anti-Aliasing (MSAA)).  
  
- Člen MipLevels je nastavený na hodnotu 1 (žádné existující Mipmap).  
  
  Když je počáteční údaje poskytnuté aplikací, formátu textury musí podporovat automatické Mipmap generování – podle D3D11_FORMAT_SUPPORT_MIP_AUTOGEN – Pokud formát není BC1, BC2 nebo BC3; v opačném případě se nezmění textury a žádné mapy mip jsou generovány, pokud je zadaný počáteční data.  
  
  Pokud mapy mip byly automaticky generovány pro textury, volání `ID3D11Device::CreateShaderResourceView` jsou upraveny během přehrávání používat řetěz mip během vzorkování textury.  
  
## <a name="example"></a>Příklad  
 **Generování Mipmap** variant možné reprodukovat pomocí kódu takto:  
  
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
  
 Vytvoření textury, který má úplný řetěz mip, nastavte `D3D11_TEXTURE2D_DESC::MipLevels` na hodnotu 0. Počet úrovní mip v úplný řetěz mip je floor(log2(n) + 1), kde n je největší dimenzi textury.  
  
 Mějte na paměti, když zadáte počáteční data `CreateTexture2D`, je nutné zadat objekt D3D11_SUBRESOURCE_DATA pro jednotlivé úrovně mip.  
  
> [!NOTE]
>  Pokud chcete poskytnout vlastní mip úrovně obsah, místo aby generovala je automaticky, musíte vytvořit vaše textury s použitím image editor, který podporuje textury pro mapovanou mip a pak načíst soubor a předat úrovní mip k `CreateTexture2D`.  
  
## <a name="see-also"></a>Viz také  
 [Varianta polovičních/čtvrtinových dimenzí textury](half-quarter-texture-dimensions-variant.md)
