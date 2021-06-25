---
title: Image Library Viewer | Microsoft Docs
description: Přečtěte si o nástroji Visual Studio Image Library Viewer, který načítá a prohledá manifesty obrázků a umožňuje zobrazit atributy obrázků a manipulovat s nimi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02e7c5d5ed45b7a6c19c248e949e667ec0a1bdc0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898707"
---
# <a name="image-library-viewer"></a>Prohlížeč knihovny obrázků
Nástroj Visual Studio Image Library Viewer může načítat a prohledávat manifesty obrázků, což uživateli umožňuje pracovat s nimi stejným způsobem jako Visual Studio. Uživatel může měnit pozadí, velikosti, dpi, vysoký kontrast a další nastavení. Nástroj také zobrazí informace o načítání pro každý manifest image a zdrojové informace pro každou image v manifestu image. Tento nástroj je užitečný pro:

1. Diagnostika chyb

2. Zajištění vlastního nastavení atributů v manifestech vlastních i image

3. Hledání obrázků v katalogu Visual Studio Image Catalog, aby rozšíření Visual Studio mohli používat obrázky, které se vejdou do stylu Visual Studio

   ![Image Library Viewer Hero](../../extensibility/internals/media/image-library-viewer-hero.png "Image Library Viewer Hero")

   **Moniker obrázku**

   Moniker obrázku (nebo zkráceně moniker) je pár GUID:ID, který jedinečně identifikuje asset obrázku nebo asset seznamu obrázků v knihovně obrázků.

   **Soubory manifestu obrázku**

   Soubory manifestu obrázku (.imagemanifest) jsou soubory XML, které definují sadu prostředků obrázku, monikery, které představují tyto prostředky, a skutečné obrázky nebo obrázky, které představují jednotlivé prostředky. Manifesty obrázků mohou definovat samostatné image nebo seznamy obrázků pro podporu starší verze uživatelského rozhraní. Kromě toho existují atributy, které je možné nastavit pro prostředek nebo na jednotlivých obrázcích za každým assetem, aby se změnily, kdy a jak se tyto prostředky zobrazují.

   **Schéma manifestu obrázku**

   Kompletní manifest obrázku vypadá asi takhle:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Symboly**

 Manifest obrázku může jako čitelnost a údržbu používat symboly pro hodnoty atributů. Symboly jsou definovány tímto kódem:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|**Dílčím**|**Definition**|
|-|-|
|Import|Importuje symboly daného souboru manifestu pro použití v aktuálním manifestu.|
|Identifikátor GUID|Symbol představuje identifikátor GUID a musí odpovídat formátování GUID.|
|ID|Symbol představuje ID a musí to být negativní celé číslo.|
|Řetězec|Symbol představuje libovolnou řetězcovou hodnotu.|

 Symboly rozlišují malá a velká písmena a odkazují se na ně pomocí syntaxe $(název-symbolu):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Některé symboly jsou předdefinované pro všechny manifesty. Ty lze použít v atributu Uri elementu \<Source> nebo \<Import> k odkazování na cesty v místním počítači.

|**Symbol**|**Popis**|
|-|-|
|CommonProgramFiles|Hodnota proměnné prostředí %CommonProgramFiles%|
|LocalAppData|Hodnota proměnné prostředí %LocalAppData%|
|ManifestFolder|Složka obsahující soubor manifestu|
|Mydocuments|Úplná cesta ke Dokumenty složky aktuálního uživatele|
|ProgramFiles|Hodnota proměnné prostředí %ProgramFiles%|
|Systémový|Složka Windows\System32|
|Windir|Hodnota proměnné prostředí %WinDir%|

 **Obrázek**

 Element \<Image> definuje image, na kterou lze odkazovat pomocí monikeru. Identifikátor GUID a ID společně tvoří moniker image. Moniker pro image musí být jedinečný v celé knihovně obrázků. Pokud má daný moniker více než jeden obrázek, první obrázek se při vytváření knihovny setká s tím, který se uchovává.

 Musí obsahovat alespoň jeden zdroj. I když zdroje neutrální velikosti poskytují nejlepší výsledky v široké škále velikostí, nejsou vyžadovány. Pokud je služba vyzvána k zobrazení obrázku o velikosti, která není definovaná v elementu a neexistuje žádný zdroj neutrální velikosti, služba zvolí zdroj s nejlepší velikostí a škáluje ji na \<Image> požadovanou velikost.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Atribut**|**Definition**|
|-|-|
|Identifikátor GUID|[Povinné] Část GUID monikeru image|
|ID|[Povinné] Část ID monikeru obrázku|
|AllowColorInversion|[Volitelné, výchozí hodnota true] Určuje, jestli může být obrázek při použití na tmavém pozadí invertován prostřednictvím kódu programu.|

 **Zdroj**

 Element \<Source> definuje jeden prostředek zdroje obrázku (XAML a PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Atribut**|**Definition**|
|-|-|
|Uri|[Povinné] Identifikátor URI, který definuje, odkud lze image načíst. Může se zobrazit některý z následujících:<br /><br /> – Identifikátor [URI balíčku](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) s využitím application:/// autority<br /><br /> – Absolutní odkaz na prostředek komponenty<br /><br /> – Cesta k souboru obsahujícímu nativní prostředek|
|Pozadí|[Volitelné] Určuje, jaký druh pozadí má být zdroj použit.<br /><br /> Může se zobrazit některý z následujících:<br /><br /> - *Light*(Světlo): Zdroj lze použít na světlém pozadí.<br /><br /> - *Dark*(Tmavý): Zdroj lze použít na tmavém pozadí.<br /><br /> - *HighContrast:* Zdroj lze použít na libovolném pozadí v Vysoký kontrast režimu.<br /><br /> - *HighContrastLight:* Zdroj lze použít na světlém pozadí v Vysoký kontrast režimu.<br /><br /> -*HighContrastDark:* Zdroj lze použít na tmavém pozadí v Vysoký kontrast režimu.<br /><br /> Pokud je **atribut Background** vynechán, zdroj lze použít na libovolném pozadí.<br /><br /> Pokud **je pozadí** *Světlý,* *Tmavý,* *HighContrastLight* nebo *HighContrastDark,* barvy zdroje se nikdy nepřevrátí. Pokud **je vlastnost Background** vynechána nebo nastavena na hodnotu *HighContrast,* je inverze barev zdroje řízena atributem **AllowColorInversion obrázku.**|

 Element \<Source> může mít přesně jeden z následujících volitelných dílčích elementů:

|**Prvek**|**Atributy (všechny povinné)**|**Definition**|
|-|-|-|
|\<Size>|Hodnota|Zdroj se použije pro obrázky dané velikosti (v jednotkách zařízení). Obrázek bude čtvercový.|
|\<SizeRange>|MinSize, MaxSize|Zdroj se použije pro obrázky z MinSize do MaxSize (v jednotkách zařízení) včetně. Obrázek bude čtvercový.|
|\<Dimensions>|Width(Šířka), Height (Výška)|Zdroj se použije pro obrázky dané šířky a výšky (v jednotkách zařízení).|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Zdroj se použije pro obrázky od minimální šířky/výšky po maximální šířku/výšku (v jednotkách zařízení) včetně.|

 Prvek může mít také volitelný dílčí prvek, který definuje , který je načten z nativního sestavení, \<Source> \<NativeResource> nikoli ze \<Source> spravovaného sestavení.

```xml
<NativeResource Type="type" ID="int" />
```

|**Atribut**|**Definition**|
|-|-|
|Typ|[Povinné] Typ nativního prostředku, XAML nebo PNG|
|ID|[Povinné] Celočíselná část ID nativního prostředku|

 **Imagelist**

 Element \<ImageList> definuje kolekci obrázků, které mohou být vráceny v jednom pruhu. Pruh je podle potřeby sestavený na vyžádání.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Atribut**|**Definition**|
|-|-|
|Identifikátor GUID|[Povinné] Část GUID monikeru image|
|ID|[Povinné] Část ID monikeru obrázku|
|Externí|[Volitelné, výchozí hodnota false] Určuje, jestli moniker obrázku odkazuje na obrázek v aktuálním manifestu.|

 Moniker obsažené image nemusí odkazovat na image definovanou v aktuálním manifestu. Pokud se obsažený obrázek v knihovně obrázků nenašel, použije se místo ní prázdný zástupný obrázek.

## <a name="how-to-use-the-tool"></a>Jak používat nástroj
 **Ověření vlastního manifestu image**

 Pokud chcete vytvořit vlastní manifest, doporučujeme k automatickém vygenerování manifestu použít nástroj ManifestFromResources. Pokud chcete vlastní manifest ověřit, spusťte Prohlížeč knihovny obrázků a vyberte Soubor > Nastavit cesty... otevřete dialogové okno Adresáře vyhledávání. Nástroj použije vyhledávací adresáře k načtení manifestů obrázků, ale použije je také k vyhledání souborů .dll, které obsahují obrázky v manifestu, takže nezapomeňte do tohoto dialogového okna zahrnout adresáře manifestu i knihovny DLL.

 ![Vyhledávání v prohlížeči knihovny obrázků](../../extensibility/internals/media/image-library-viewer-search.png "Vyhledávání v prohlížeči knihovny obrázků")

 Kliknutím **na Přidat...** vyberte nové adresáře hledání a vyhledejte manifesty a jejich odpovídající knihovny DLL. Nástroj si tyto vyhledávací adresáře zapamatuje a můžete je zapnout nebo vypnout zaškrtnutím nebo zrušením zaškrtnutí adresáře.

 Ve výchozím nastavení se nástroj pokusí najít adresář Visual Studio a přidat tyto adresáře do seznamu adresářů hledání. Adresáře, které nástroj nenajde, můžete přidat ručně.

 Po načtení všech manifestů je možné pomocí tohoto  nástroje přepínat barvy pozadí,  **DPI,** vysoký kontrast nebo šedé škálování obrázků, aby uživatel mohl vizuálně zkontrolovat prostředky obrázků a ověřit, že se správně vykreslují z různých nastavení.

 ![Pozadí prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-background.png "Pozadí prohlížeče knihovny obrázků")

 Barvu pozadí můžete nastavit na Světlý, Tmavý nebo na vlastní hodnotu. Výběrem možnosti Vlastní barva se otevře dialogové okno pro výběr barvy a přidání této vlastní barvy do dolní části pole se seznamem pozadí pro pozdější snadné odvolání.

 ![Vlastní barva prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-custom-color.png "Vlastní barva prohlížeče knihovny obrázků")

 Když vyberete moniker obrázku, zobrazí se informace o každém skutečném obrázku za monikerem v podokně Podrobnosti obrázku na pravé straně. Podokno také umožňuje uživatelům zkopírovat moniker podle názvu nebo nezpracované hodnoty GUID:ID.

 ![Podrobnosti o obrázku v prohlížeči knihovny obrázků](../../extensibility/internals/media/image-library-viewer-image-details.png "Podrobnosti o obrázku v prohlížeči knihovny obrázků")

 Informace zobrazené pro každý zdroj bitové kopie zahrnují, na jaký druh pozadí se má zobrazit, jestli je možné je zacílí nebo podporuje Vysoký kontrast, jaké velikosti jsou platné nebo jestli je velikost neutrální a jestli image pochází z nativního sestavení.

 ![Motiv Lze zobrazit v prohlížeči knihovny obrázků](../../extensibility/internals/media/image-library-viewer-can-theme.png "Motiv Lze zobrazit v prohlížeči knihovny obrázků")

 Při ověřování manifestu image doporučujeme nasadit manifest a knihovnu DLL image v jejich reálných umístěních. Tím se ověří, že všechny relativní cesty fungují správně a že knihovna obrázků může najít a načíst manifest a knihovnu DLL image.

 **Hledání známých monikerů v katalogu obrázků**

 Aby bylo možné Visual Studio styly, rozšíření Visual Studio může místo vytváření a používání vlastního Visual Studio použít obrázky v katalogu Visual Studio Image Catalog. To má výhodu, že tyto obrázky nemusíme udržovat, a zaručuje, že obrázek bude mít zálohovací obrázek s vysokým rozlišením DPI, takže by měl vypadat správně ve všech nastaveních DPI, která Visual Studio podporuje.

 Prohlížeč knihovny obrázků umožňuje prohledávat manifest, aby uživatel mohl najít moniker představující asset obrázku a použít tento moniker v kódu. Pokud chcete hledat obrázky, zadejte do vyhledávacího pole požadovaný hledaný termín a stiskněte Klávesu Enter. Na stavovém řádku v dolní části se zobrazí, kolik shod bylo nalezeno z celkového počtu obrázků ve všech manifestech.

 ![Filtr prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-filter.png "Filtr prohlížeče knihovny obrázků")

 Při hledání monikerů obrázků v existujících manifestech doporučujeme vyhledat a používat pouze monikery katalogu obrázků Visual Studio, jiné záměrně veřejně přístupné monikery nebo vlastní monikery. Pokud používáte neveřejné monikery, může dojít k poruše vlastního uživatelského rozhraní nebo neočekávaným způsobem změnit jeho obrázky, pokud se tyto neveřejné monikery a obrázky změní nebo aktualizují.

 Kromě toho je možné vyhledávat podle identifikátoru GUID. Tento typ vyhledávání je užitečný pro filtrování seznamu do jednoho manifestu nebo jednoho pododdílu manifestu, pokud tento manifest obsahuje více identifikátorů GUID.

 ![Guid filtru prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Guid filtru prohlížeče knihovny obrázků")

 A konečně je také možné vyhledávat podle ID.

 ![ID filtru prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-filter-id.png "ID filtru prohlížeče knihovny obrázků")

## <a name="notes"></a>Poznámky

- Ve výchozím nastavení nástroj nastáhne několik manifestů image přítomných v adresáři Visual Studio instalace. Jediný, který má veřejně použitelné monikery, je manifest **Microsoft.VisualStudio.ImageCatalog.** GUID: ae27a6b0-e345-4288-96df-5eaf394ee369  (nepřepište tento identifikátor GUID ve vlastním manifestu) Typ: KnownMonikers

- Nástroj se pokusí při spuštění načíst všechny manifesty obrázků, které najde, takže může trvat několik sekund, než se aplikace skutečně zobrazí. Může také být pomalý nebo nereagující při načítání manifestů.

## <a name="sample-output"></a>Vzorový výstup
 Tento nástroj negeneruje žádný výstup.
