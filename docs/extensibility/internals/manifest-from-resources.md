---
title: Manifest from Resources | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ea5931c77e267bc6065693be1ae144c250ce6df
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536225"
---
# <a name="manifest-from-resources"></a>Manifest z prostředků
Nástroj Manifest from Resources je Konzolová aplikace, která přebírá seznam prostředků obrázků (soubory. png nebo. XAML) a generuje soubor. imagemanifest, který umožňuje použití těchto imagí ve službě image sady Visual Studio. Kromě toho lze pomocí tohoto nástroje Přidat obrázky do existujícího. imagemanifest. Tento nástroj je užitečný pro přidání vysokého rozlišení DPI a podpory pro obrázky do rozšíření sady Visual Studio. Vygenerovaný soubor. imagemanifest by měl být součástí a nasazen jako součást rozšíření sady Visual Studio (. vsix).

## <a name="how-to-use-the-tool"></a>Jak používat nástroj
 **Syntax**

 ManifestFromResources/Resources: \<Dir1> ; \<Img1> /Assembly je: \<AssemblyName>\<Optional Args>

 **Arguments**

|**Název přepínače**|**Poznámky**|**Povinné nebo volitelné**|
|-|-|-|
|/resources|Seznam obrázků nebo adresářů oddělených středníkem. Tento seznam by měl vždycky obsahovat úplný seznam imagí, které budou v manifestu. Pokud je zadaný jenom částečný seznam, ztratí se položky, které nejsou zahrnuté.<br /><br /> Pokud je daný soubor prostředků pruhem obrázku, nástroj ho rozdělí do samostatných imagí před přidáním každého dílčího obrázku do manifestu.<br /><br /> Pokud je obrázek souborem. png, doporučujeme tento název naformátovat tak, aby nástroj mohl vyplnit správné atributy obrázku: \<Name> . \<Width> . \<Height> . PNG.|Vyžadováno|
|/Assembly je|Název spravovaného sestavení (nezahrnuje rozšíření) nebo cesta modulu runtime nativního sestavení, které hostuje prostředky (vzhledem k umístění modulu runtime manifestu).|Vyžadováno|
|/manifest|Název, který má být vygenerován souboru. imagemanifest. To může také zahrnovat absolutní nebo relativní cestu k vytvoření souboru v jiném umístění. Výchozí název odpovídá názvu sestavení.<br /><br /> Výchozí: \<Current Directory> \\<Assembly \> . imagemanifest|Volitelné|
|/guidName|Název, který má být zadán pro symbol identifikátoru GUID pro všechny obrázky ve vygenerovaném manifestu.<br /><br /> Výchozí: AssetsGuid|Volitelné|
|/rootPath|Kořenová cesta, kterou je třeba před vytvořením identifikátorů URI spravovaného prostředku odepsat. (Tento příznak vám pomůže s případy, kdy nástroj získá neoprávněnou cestu k relativnímu identifikátoru URI, což způsobí selhání načtení prostředků.)<br /><br /> Výchozí\<Current Directory>|Volitelné|
|/Recursive|Nastavením tohoto příznaku sdělíte nástroji rekurzivní hledání adresářů v argumentu/Resources. Vynechání tohoto příznaku způsobí, že se adresáře budou hledat jenom na nejvyšší úrovni.|Volitelné|
|/isNative|Pokud je argumentem sestavení cesta k nativnímu sestavení, nastavte tento příznak. Tento příznak vynechejte, pokud je argumentem sestavení název spravovaného sestavení. (Další informace o tomto příznaku najdete v části poznámky.)|Volitelné|
|/newGuids|Nastavením tohoto příznaku se dozvíte, že nástroj vytvoří novou hodnotu pro symbol GUID obrázku, místo abyste museli sloučit z existujícího manifestu.|Volitelné|
|/newIds|Nastavením tohoto příznaku se dozvíte, že nástroj vytvoří nové hodnoty symbolů ID pro každý obrázek místo sloučení hodnot z existujícího manifestu.|Volitelné|
|/noLogo|Nastavením tohoto příznaku se zastaví tisk informací o produktech a copyrightech.|Volitelné|
|/?|Vytiskněte informace o nápovědě.|Volitelné|
|/help|Vytiskněte informace o nápovědě.|Volitelné|

 **Příklady**

- ManifestFromResources/Resources: D:\Images/Assembly je: My. Assembly. Name/isNative

- ManifestFromResources/resources:D:\Images\Image1.png;D: \Images\Image1.xaml/Assembly je: My. Assembly. Name/manifest: MyImageManifest. imagemanifest

- ManifestFromResources/resources:D:\Images\Image1.png;D: \Images\Image1.xaml/Assembly je: My. Assembly. Name/guidName: MyImages/newGuids/newIds

## <a name="notes"></a>Poznámky

- Nástroj podporuje pouze soubory. png a. XAML. Všechny ostatní typy obrázků nebo souborů budou ignorovány. Pro všechny nepodporované typy zjištěné při analýze prostředků se vygeneruje upozornění. Pokud se po dokončení analýzy prostředků nenaleznou žádné podporované image, vygeneruje se chyba.

- Podle navrženého formátu pro obrázky. png nástroj nastaví hodnotu velikost/dimenze pro formát. png na velikost zadanou velikostí, a to i v případě, že se liší od skutečné velikosti obrázku.

- Formát Width/Height lze pro obrázky. png vynechat, ale nástroj si přečte skutečnou šířku a výšku obrázku a použije je pro hodnotu velikosti a dimenze obrázku.

- Spuštění tohoto nástroje na stejném svazku s obrázkem několikrát pro stejný svazek. imagemanifest bude mít za následek duplicitní položky manifestu, protože se nástroj pokusí rozdělit obrázek do samostatných imagí a přidat je do existujícího manifestu.

- Sloučení (vynechání/newGuids nebo/newIds) by mělo být provedeno pouze pro manifesty vygenerované nástrojem. Manifesty, které byly přizpůsobené nebo vygenerované prostřednictvím jiných prostředků, se nemusí správně sloučit.

- Manifesty, které jsou generovány pro nativní sestavení, mohou být po generaci ručně upravovány, aby se symboly ID shodovaly s ID prostředků ze souboru. RC nativního sestavení.

## <a name="sample-output"></a>Vzorový výstup
 **Jednoduchý manifest obrázku**

 Manifest obrázku bude podobný tomuto souboru. XML:

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

 **Manifest obrázku pro pruh obrázku**

 Manifest obrázku pro pruh obrázku bude podobný tomuto souboru. XML:

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

 **Manifest obrázku pro prostředky nativního bitové kopie sestavení**

 Manifest obrázku pro nativní bitové kopie bude vypadat podobně jako tento soubor. XML:

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
