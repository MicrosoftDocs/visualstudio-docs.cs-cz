---
title: Manifest ze zdrojů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb853963cc5ca6fbe6080249daa8fcf9c08bf943
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707282"
---
# <a name="manifest-from-resources"></a>Manifest z prostředků
Nástroj Manifest from Resources je konzolová aplikace, která přebírá seznam obrazových prostředků (.png nebo .xaml files) a generuje soubor .imagemanifest, který umožňuje použití těchto obrázků se službou Visual Studio Image Service. Kromě toho tento nástroj lze přidat obrázky do existujícího .imagemanifest. Tento nástroj je užitečný pro přidání podpory vysokého DPI a témat pro obrázky do rozšíření sady Visual Studio. Generovaný soubor .imagemanifest by měl být zahrnut a nasazen jako součást rozšíření sady Visual Studio (.vsix).

## <a name="how-to-use-the-tool"></a>Jak nástroj používat
 **Syntaxe**

 ManifestFromResources /resources:\<Dir1>; \<Img1> /assembly:\< \<AssemblyName> volitelné> Args

 **Argumenty**

||||
|-|-|-|
|**Název přepínače**|**Poznámky**|**Povinné nebo volitelné**|
|/zdroje|Středník-oddělený seznam obrázků nebo adresářů. Tento seznam by měl vždy obsahovat úplný seznam obrázků, které budou v manifestu. Pokud je uveden pouze částečný seznam, položky, které nejsou zahrnuty, budou ztraceny.<br /><br /> Pokud je daný soubor prostředků proužkem obrázku, nástroj jej před přidáním každého podobrazu do manifestu rozdělí na samostatné obrazy.<br /><br /> Pokud se jedná o soubor PNG, doporučujeme naformátovat název takto, aby nástroj mohl \<vyplnit správné atributy obrázku: Název>. \<Šířka>. \<Výška>.png.|Požaduje se|
|/sestavení|Název spravovaného sestavení (bez rozšíření) nebo cesta runtime nativního sestavení, které hostuje prostředky (vzhledem k umístění za běhu manifestu).|Požaduje se|
|/manifest|Název, který má být poskytnut generovanému souboru .imagemanifest. To může také zahrnovat absolutní nebo relativní cestu k vytvoření souboru v jiném umístění. Výchozí název odpovídá názvu sestavení.<br /><br /> Výchozí: \<Aktuální \\>\>adresáře<sestavení .imagemanifest|Nepovinné|
|/guidNázev|Název, který má být přidělen symbolu GUID pro všechny obrázky ve generovaném manifestu.<br /><br /> Výchozí: AssetsGuid|Nepovinné|
|/rootPath|Kořenová cesta, kterou je třeba před vytvořením spravovaných identifikátorů URI odebrat. (Tento příznak je pomoci s případy, kdy nástroj získá relativní cestu URI špatně, což způsobuje, že prostředky se nezdaří načíst.)<br /><br /> Výchozí: \<Aktuální> adresářů|Nepovinné|
|/rekurzivní|Nastavení tohoto příznaku říká nástroj rekurzivně prohledávat všechny adresáře v /resources argument. Vynechání této vlajky bude mít za následek pouze nejvyšší úroveň hledání adresářů.|Nepovinné|
|/isNative|Nastavte tento příznak, pokud je argument sestavení cestou pro nativní sestavení. Vynechat tento příznak, když argument sestavení je název spravovaného sestavení. (Další informace o tomto příznaku naleznete v části Poznámky.)|Nepovinné|
|/nové Guidy|Nastavení tohoto příznaku říká nástroji vytvořit novou hodnotu pro symbol GUID obrázků namísto sloučení z existujícího manifestu.|Nepovinné|
|/newIds|Nastavení tohoto příznaku říká nástroji vytvořit nové hodnoty symbolů ID pro každý obrázek namísto slučování hodnot z existujícího manifestu.|Nepovinné|
|/noLogo|Nastavení tohoto příznaku zabrání tisku informací o produktech a autorských právech.|Nepovinné|
|/?|Vytiskněte informace nápovědy.|Nepovinné|
|/help|Vytiskněte informace nápovědy.|Nepovinné|

 **Příklady**

- ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Poznámky

- Nástroj podporuje pouze soubory PNG a .xaml. Všechny ostatní typy obrázků nebo souborů budou ignorovány. Upozornění je generováno pro všechny nepodporované typy zjištěné při analýzě prostředků. Pokud po dokončení analýzy prostředků nástroj nenajdete žádné podporované obrázky, bude vygenerována chyba.

- Podle navrhovaného formátu pro obrázky PNG nastaví nástroj hodnotu velikosti/dimenze pro png na velikost zadanou formátem, i když se liší od skutečné velikosti obrázku.

- Formát šířky a výšky lze vynechat pro obrázky PNG, ale nástroj přečte skutečnou šířku/výšku obrázku a použije je pro hodnotu velikosti/kóty obrázku.

- Spuštění tohoto nástroje na stejném proužku obrázku vícekrát pro stejný .imagemanifest bude mít za následek duplicitní položky manifestu, protože nástroj se pokusí rozdělit proužka obrazu do samostatných obrazů a přidat je do existujícího manifestu.

- Sloučení (vynechání /newGuids nebo /newIds) by mělo být provedeno pouze pro manifesty generované nástrojem. Manifesty, které byly přizpůsobeny nebo generovány jinými prostředky, nemusí být správně sloučeny.

- Manifesty, které jsou generovány pro nativní sestavení může být nutné ručně upravit po generování, aby se symboly ID odpovídaly ID prostředků ze souboru .rc nativního sestavení.

## <a name="sample-output"></a>Vzorový výstup
 **Jednoduchý manifest obrázku**

 Manifest obrázku bude podobný tomuto souboru XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImage" Value="0" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```

 **Manifest obrázku pro obrazový proužek**

 Manifest obrazu pro proužka obrázku bude podobný tomuto souboru XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImageStrip_0" Value="1" />
    <ID Name="MyImageStrip_1" Value="2" />
    <ID Name="MyImageStrip" Value="3" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">
      <Source Uri="$(Resources)/MyImageStrip_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">
      <Source Uri="$(Resources)/MyImageStrip_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists>
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />
    </ImageList>
  </ImageLists>
</ImageManifest>
```

 **Manifest obrázku pro nativní prostředky obrazu sestavení**

 Manifest obrázku pro nativní obrazy bude podobný tomuto souboru XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15198 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />
    <ID Name="MyImage1" Value="0" />
    <ID Name="MyImage2" Value="1" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage1)" Type="PNG" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage2)" Type="PNG" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```
