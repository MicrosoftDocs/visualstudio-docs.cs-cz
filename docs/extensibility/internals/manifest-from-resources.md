---
title: Manifest from Resources | Microsoft Docs
description: Naučte se používat nástroj Manifest from Resources k přidání souborů .png nebo .xaml do souboru .imagemanifest pro použití se službou Visual Studio Image Service.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f69a46362b3076025a63625adb1ee4a478622259
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903175"
---
# <a name="manifest-from-resources"></a>Manifest z prostředků
Nástroj Manifest from Resources je konzolová aplikace, která přebírá seznam prostředků obrázků (soubory .png nebo .xaml) a generuje soubor .imagemanifest, který umožňuje použití těchto imagí se službou Visual Studio Image Service. Kromě toho lze tento nástroj použít k přidání imagí do existujícího souboru .imagemanifest. Tento nástroj je užitečný pro přidání podpory vysokých hodnot DPI a nastavení pro obrázky do Visual Studio rozšíření. Vygenerovaný soubor .imagemanifest by měl být zahrnutý v souboru a nasazený jako součást Visual Studio souboru (.vsix).

## <a name="how-to-use-the-tool"></a>Jak používat nástroj
 **Syntax**

 ManifestFromResources /resources: \<Dir1> ; \<Img1> /assembly: \<AssemblyName>\<Optional Args>

 **Argumenty**

|**Název přepínače**|**Poznámky**|**Povinné nebo Volitelné**|
|-|-|-|
|/resources|Seznam obrázků nebo adresářů oddělených středníkem. Tento seznam by měl vždy obsahovat úplný seznam imagí, které budou v manifestu. Pokud je uveden pouze částečný seznam, položky, které nejsou zahrnuty, budou ztraceny.<br /><br /> Pokud je daný soubor prostředků proužek obrázků, nástroj ho před přidáním každého dílčího image do manifestu rozdělí na samostatné obrázky.<br /><br /> Pokud je obrázek souborem .png, doporučujeme formátovat název tak, aby nástroj mohl vyplnit správné atributy obrázku: \<Name> . \<Width> . \<Height>.png.|Vyžadováno|
|/assembly|Název spravovaného sestavení (bez přípony) nebo cesta modulu runtime nativního sestavení, které je hostitelem prostředků (vzhledem k umístění modulu runtime manifestu).|Vyžadováno|
|/manifest|Název, který má být přiřazen vygenerovaný soubor .imagemanifest. To může také zahrnovat absolutní nebo relativní cestu k vytvoření souboru v jiném umístění. Výchozí název odpovídá názvu sestavení.<br /><br /> Výchozí: \<Current Directory> \\<sestavení \> .imagemanifest|Volitelné|
|/guidName|Název, který se má dát symbolu GUID pro všechny obrázky ve vygenerované manifestu.<br /><br /> Výchozí hodnota: AssetsGuid|Volitelné|
|/rootPath|Kořenovou cestu, kterou je potřeba před vytvořením identifikátorů URI spravovaných prostředků odizolovat. (Tento příznak pomáhá s případy, kdy nástroj získá nesprávnou cestu k relativnímu identifikátoru URI, což způsobí, že se prostředky nepodaří načíst.)<br /><br /> Výchozí: \<Current Directory>|Volitelné|
|/recursive|Nastavení tohoto příznaku říká nástroji, aby rekurzivně prohledává všechny adresáře v argumentu /resources. Vynechání tohoto příznaku bude mít za následek hledání adresářů pouze na nejvyšší úrovni.|Volitelné|
|/isNative|Tento příznak nastavte, pokud je argument sestavení cestou pro nativní sestavení. Vynechat tento příznak, pokud je argument sestavení název spravovaného sestavení. (Další informace o tomto příznaku najdete v části Poznámky.)|Volitelné|
|/newGuids|Nastavení tohoto příznaku říká nástroji, aby místo sloučení hodnoty z existujícího manifestu vytvořil novou hodnotu pro symbol GUID obrázků.|Volitelné|
|/newIds|Nastavení tohoto příznaku říká nástroji, aby pro každý obrázek vytvořil nové hodnoty symbolů ID místo sloučení hodnot z existujícího manifestu.|Volitelné|
|/noLogo|Nastavení tohoto příznaku zastaví tisk informací o produktu a autorských právech.|Volitelné|
|/?|Vytiskněte informace nápovědy.|Volitelné|
|/help|Vytiskněte informace nápovědy.|Volitelné|

 **Příklady**

- ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Poznámky

- Nástroj podporuje pouze soubory .png a .xaml. Všechny ostatní typy obrázků nebo souborů budou ignorovány. Pro všechny nepodporované typy, ke kterým došlo při analýze prostředků, se vygeneruje upozornění. Pokud se po dokončení analýzy prostředků nástroje nenašly žádné podporované image, vygeneruje se chyba.

- Podle navrhovaného formátu pro obrázky .png nástroj nastaví velikost nebo hodnotu dimenze pro .png na zadanou velikost, i když se liší od skutečné velikosti obrázku.

- Formát šířky a výšky lze pro obrázky .png vynechat, ale nástroj přečte skutečnou šířku a výšku obrázku .png použije je pro velikost obrázku nebo hodnotu dimenze.

- Spuštění tohoto nástroje na stejném pásu obrázků několikrát pro stejný soubor .imagemanifest bude mít za následek duplicitní položky manifestu, protože se nástroj pokusí rozdělit pruh obrázků na samostatné image a přidat je do existujícího manifestu.

- Sloučení (vynechání /newGuids nebo /newIds) by se mělo provést pouze pro manifesty generované nástrojem. Manifesty, které byly přizpůsobeny nebo generovány jiným způsobem, nemusí být správně sloučeny.

- Manifesty, které jsou generovány pro nativní sestavení, mohou být po vygenerování ručně upraveny, aby symboly ID odpovídaly ID prostředků ze souboru .rc nativního sestavení.

## <a name="sample-output"></a>Vzorový výstup
 **Jednoduchý manifest obrázku**

 Manifest image bude podobný tomuto .xml souboru:

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

 **Manifest obrázku pro pruh obrázků**

 Manifest obrázku pro proužek obrázků bude podobný tomuto .xml souboru:

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

 **Manifest bitové kopie pro prostředky nativní bitové kopie sestavení**

 Manifest bitové kopie pro nativní bitové kopie bude podobný tomuto .xml souboru:

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
