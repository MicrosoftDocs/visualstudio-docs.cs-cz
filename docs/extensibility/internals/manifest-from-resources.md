---
title: Z prostředků manifestu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 514135e5c6ba932d7b3b4319dd39c1df4e8cb212
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134278"
---
# <a name="manifest-from-resources"></a>Manifestu z prostředků
Manifest z prostředků nástroje je konzolovou aplikaci, která přebírá seznam prostředky obrázků (.png nebo XAML soubory) a vygeneruje soubor .imagemanifest, který umožňuje tyto bitové kopie pro použití s Visual Studio Service bitové kopie. Kromě toho tento nástroj slouží k přidání bitové kopie do existující .imagemanifest. Tento nástroj je užitečný pro přidání podporu pro bitové kopie do rozšíření pro Visual Studio vysokou hodnotou DPI a motivů. Soubor generovaný .imagemanifest by měl součástí a nasadit jako součást rozšíření sady Visual Studio (VSIX).  
  
## <a name="how-to-use-the-tool"></a>Postup použití nástroje  
 **Syntaxe**  
  
 ManifestFromResources /resources:\<Dir1 >;\< Img1 > /assembly:\<AssemblyName > \<volitelné argumenty >  
  
 **Argumenty**  
  
||||  
|-|-|-|  
|**Název přepínače**|**Poznámky**|**Požadované nebo volitelné**|  
|/Resources|Seznam oddělený středníkem bitové kopie nebo adresáře. Tento seznam by měla vždycky obsahovat úplný seznam bitové kopie, které budou v manifestu. Pokud je zadána částečný seznam, jen položky nejsou zahrnuty budou ztraceny.<br /><br /> Pokud je soubor daný prostředek pruhu bitové kopie, nástroj rozdělí se na samostatné Image před přidáním každý subimage k manifestu.<br /><br /> Pokud je bitová kopie soubor PNG, doporučujeme formátovat název, jako je to tak, aby tento nástroj můžete vyplnit správné atributy pro bitovou kopii: \<Name >.\< Šířka >. \<Výška > PNG.|Požadováno|  
|/Assembly|Název spravované sestavení (včetně není rozšíření) nebo cestu runtime nativní sestavení, který je hostitelem prostředky (relativní vůči v manifestu modulu runtime umístění).|Požadováno|  
|/ manifest|Název generované .imagemanifest souboru. To může zahrnovat absolutní nebo relativní cesta k vytvoření souboru v jiném umístění. Výchozí název odpovídá názvu sestavení.<br /><br /> Výchozí hodnota: \<aktuální adresář >\\< sestavení\>.imagemanifest|Nepovinné|  
|/guidName|Název umožnit symbolu identifikátor GUID pro všechny bitové kopie v vygenerovaný manifest.<br /><br /> Výchozí: AssetsGuid|Nepovinné|  
|/rootPath|Kořenová cesta, kterou je potřeba se odstraní před vytvořením spravovaných prostředků identifikátory URI. (Tento příznak je pomoct s případy, kdy nástroj získá relativní cestou URI nesprávný způsobuje materiály, které se nepovedlo načíst.)<br /><br /> Výchozí hodnota: \<aktuální adresář >|Nepovinné|  
|/ Recursive|Nastavením tohoto příznaku informuje nástroj k rekurzivnímu hledání všechny adresáře v argumentu /resources. Vynechání tento příznak bude mít za následek top-úrovně jen vyhledávání adresářů.|Nepovinné|  
|/isNative|Tento příznak nastavte, když argument sestavení je cesta pro nativní sestavení. Vynechte tento příznak, když sestavení je název spravované sestavení. (Naleznete v části poznámky Další informace o tento příznak.)|Nepovinné|  
|/newGuids|Nastavením tohoto příznaku informuje nástroj pro vytvoření nové hodnoty pro bitové kopie GUID symbol místo slučování ze stávající manifestu.|Nepovinné|  
|/newIds|Nastavením tohoto příznaku informuje nástroj pro vytvoření nové hodnoty symbolu ID pro každý image místo slučování hodnoty z existující manifestu.|Nepovinné|  
|/ nologo|Nastavením tohoto příznaku zastaví informace o produktu a autorských právech v tisku.|Nepovinné|  
|/?|Vytiskněte informace nápovědy.|Nepovinné|  
|/help|Vytiskněte informace nápovědy.|Nepovinné|  
  
 **Příklady**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Poznámky  
  
-   Tento nástroj podporuje pouze soubory PNG a XAML. U jiných typů bitovou kopii nebo souboru budou ignorovány. Pro všechny nepodporované typy došlo při analýze prostředky se generuje upozornění. Když není podporováno obrázky se nacházejí dokončení nástroj Analýza prostředky, bude generována chyba  
  
-   Pomocí následujících doporučený formát pro bitové kopie, PNG, nástroj nastaví hodnota velikost nebo dimenze .png velikost zadaný formát i v případě, že se liší od skutečná velikost obrázku.  
  
-   Formát šířky a výšky lze vynechat pro bitové kopie, PNG, ale nástroj čtení obrázku skutečné šířky a výšky a použít pro hodnotu dimenze nebo velikosti obrázku.  
  
-   Tento nástroj systémem stejnou bitovou kopii pruhu vícekrát pro stejné .imagemanifest způsobí duplicitní položky manifestu, protože nástroj pokusí rozdělit pruhu bitové kopie na samostatné Image a přidejte je do existující manifest.  
  
-   Slučování (s vynecháním /newGuids nebo /newIds) lze provádět pouze pro nástroj generuje manifesty. Manifesty, které jsou přizpůsobené nebo generované jinými způsoby. nemusí být správně sloučit.  
  
-   Manifesty, které jsou generovány pro nativní sestavení může být potřeba ručně upravovat po generování aby symboly ID shodovat s ID ze souboru .rc nativní sestavení prostředků.  
  
## <a name="sample-output"></a>Vzorový výstup  
 **Jednoduchý obrázek manifestu**  
  
 Image manifest bude vypadat podobně jako tento soubor XML:  
  
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
  
 **Obrázek manifestu pro pruhu bitové kopie**  
  
 Manifest bitové kopie pro pruhu image bude vypadat podobně jako tento soubor XML:  
  
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
  
 **Obrázek manifestu pro prostředky obrázků nativní sestavení**  
  
 Manifest bitové kopie pro nativní bitové kopie bude vypadat podobně jako tento soubor XML:  
  
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