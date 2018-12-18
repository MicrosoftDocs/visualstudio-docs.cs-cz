---
title: Manifest z prostředků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d442686ab588932cac077a0b5fdc09a1a746c3d3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771859"
---
# <a name="manifest-from-resources"></a>Manifest z prostředků
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Manifest z prostředků nástroje je konzolová aplikace, která přebírá seznam prostředků obrázků (.png nebo .xaml soubory) a vygeneruje .imagemanifest soubor, který umožňuje tyto Image se použije ve službě Visual Studio bitové kopie. Kromě toho tento nástroj lze přidat Image do existujícího .imagemanifest. Tento nástroj je užitečný pro přidání podporu vysokých hodnot DPI a motivy pro bitové kopie do rozšíření aplikace Visual Studio. Soubor generovaný .imagemanifest by součástí a nasazen jako součást rozšíření sady Visual Studio (VSIX).  
  
## <a name="how-to-use-the-tool"></a>Jak používat nástroj  
 **Syntaxe**  
  
 ManifestFromResources /resources:\<Dir1 >;\< Img1 >/Assembly:\<AssemblyName > \<volitelné argumenty >  
  
 **Argumenty**  
  
||||  
|-|-|-|  
|**Název přepínače**|**Poznámky**|**Požadované nebo volitelné**|  
|/Resources|Středníkem oddělený seznam imagí nebo adresáře. Tento seznam by měl vždy obsahovat seznam všech imagí, které budou v manifestu. -Li zadána je částečný seznam, jen položky nejsou zahrnuty budou ztraceny.<br /><br /> Pokud je soubor daný prostředek obrázku, nástroj bude ho rozdělte do samostatné obrázky před přidáním každý subimage do manifestu.<br /><br /> Pokud na obrázku je soubor ve formátu PNG, doporučujeme formát názvu tímto způsobem tak, aby nástroj můžete přejít k vyplnění správné atributy pro image: \<název >.\< Šířka >. \<Výška > PNG.|Požadováno|  
|/ Assembly|Název spravovaného sestavení (nikoli včetně přípony) nebo cesta k modulu runtime nativní sestavení, který je hostitelem zdroje (relativní k umístění manifestu modulu runtime).|Požadováno|  
|Volba/manifest|Název souboru generovaného .imagemanifest. To může zahrnovat absolutní nebo relativní cestu k vytvoření souboru v jiném umístění. Výchozí název odpovídá názvu sestavení.<br /><br /> Výchozí hodnota: \<aktuální adresář >\\< sestavení\>.imagemanifest|volitelná,|  
|/guidName|Název symbolu identifikátor GUID pro všechny Image v generovaném manifestu.<br /><br /> Výchozí: AssetsGuid|volitelná,|  
|/rootPath|Kořenová cesta, kterou je potřeba se odstraní před vytvořením spravovaného prostředku identifikátorů URI. (Tento příznak je pomoct s případy, kde nástroj získá relativní cestou URI chybný, způsobí prostředky na nepodaří zavést.)<br /><br /> Výchozí hodnota: \<aktuální adresář >|volitelná,|  
|/ Recursive|Nastavení tohoto příznaku instruuje nástroj rekurzivně prohledávat všechny adresáře v argumentu /resources. Tento příznak vynechání způsobí top-úrovně pouze pro vyhledávání adresářů.|volitelná,|  
|/isNative|Tento příznak nastavte, když je argumentem sestavení cestu pro nativní sestavení. Název spravovaného sestavení po sestavení argument vynechat, nechte tento příznak. (Viz část poznámky pro další informace o tento příznak.)|volitelná,|  
|/newGuids|Nastavení tohoto příznaku instruuje nástroj pro vytvoření nové hodnoty pro symbol GUID obrázky místo sloučení z existujícího manifestu.|volitelná,|  
|/newIds|Nastavení tohoto příznaku dává pokyn k vytvoření nové hodnoty symbolů ID pro každý obrázek namísto sloučení hodnoty z existujícího manifestu nástroj.|volitelná,|  
|/ nologo|Informace o produktu a autorská práva tisk nastavení tohoto příznaku se zastaví.|volitelná,|  
|/?|Vytiskne informace nápovědy.|volitelná,|  
|/help|Vytiskne informace nápovědy.|volitelná,|  
  
 **Příklady**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Poznámky  
  
-   Nástroj podporuje jenom soubory ve formátu PNG a .xaml. U jiných typů souboru bitové kopie nebo se budou ignorovat. Vygeneruje se upozornění pro všechny nepodporované typy při analýze prostředky. Pokud ne, podporovány bitové kopie se nacházejí dokončení nástroj Analýza kódu prostředky, bude vygenerována chyba  
  
-   Pomocí následujících navrhované formátu pro obrázky ve formátu PNG, nástroj nastaví hodnota velikosti/dimenze ve formátu PNG velikosti určený formát i v případě, že se liší od skutečné velikosti na obrázku.  
  
-   Lze vynechat šířky a výšky formátu pro obrázky ve formátu PNG, ale nástroj číst skutečné šířky a výšky na obrázku, který se použijí pro hodnotu velikosti/dimenze na obrázku.  
  
-   Spuštění tohoto nástroje na stejné obrázku více než jednou pro stejný .imagemanifest způsobí duplicitní položky manifestu, protože se nástroj pokusí rozdělení obrázku na samostatné obrázky a přidat do existující manifest.  
  
-   Sloučení (vynechání /newGuids nebo /newIds) lze provádět pouze pro nástroj vygeneruje manifesty. Manifestů, které jste přizpůsobili nebo vygenerované pomocí jiným způsobem nemusí správně sloučit.  
  
-   Manifesty, které jsou generovány pro nativní sestavení možná bude nutné ručně upravit po vygenerování aby symboly ID odpovídat ID ze souboru .rc nativní sestavení prostředků.  
  
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
  
 **Obrázek manifest pro obrázku**  
  
 Manifest image pro obrázku bude vypadat podobně jako tento soubor XML:  
  
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
  
 **Manifest Image pro prostředky sestavení nativní bitové kopie**  
  
 Manifest image pro nativní bitové kopie bude vypadat podobně jako tento soubor XML:  
  
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

