---
title: Prohlížeč knihovny obrázků | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7c5eda24c235cddec99cb5177c6ed315978bc6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707751"
---
# <a name="image-library-viewer"></a>Prohlížeč knihovny obrázků
Nástroj Prohlížeč obrázků sady Visual Studio může načítat a vyhledávat manifesty obrázků, což uživateli umožňuje s nimi manipulovat stejným způsobem jako v sadě Visual Studio. Uživatel může měnit pozadí, velikosti, DPI, vysoký kontrast a další nastavení. Nástroj také zobrazuje informace o načítání pro každý manifest obrazu a zobrazuje zdrojové informace pro každý obrázek v manifestu obrazu. Tento nástroj je užitečný pro:

1. Diagnostika chyb

2. Zajištění správného nastavení atributů v manifestech vlastních obrázků

3. Hledání obrázků v katalogu obrázků sady Visual Studio, aby rozšíření sady Visual Studio bylo možné použít obrázky, které odpovídají stylu sady Visual Studio

   ![Hrdina prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-hero.png "Hrdina prohlížeče knihovny obrázků")

   **Zástupná název obrázku**

   Zástupný název obrázku (zkráceně zástupný název) je dvojice GUID:ID, která jednoznačně identifikuje datový zdroj obrázku nebo datový zdroj seznamu obrázků v knihovně obrázků.

   **Soubory manifestu obrázku**

   Soubory manifestu obrazu (.imagemanifest) jsou soubory XML, které definují sadu obrazových datových zdrojů, zástupné názvy, které představují tyto datové zdroje, a skutečný obraz nebo obrazy, které představují každý datový zdroj. Manifesty obrázků můžete definovat samostatné obrázky nebo seznamy obrázků pro podporu staršího uznatých. Kromě toho existují atributy, které lze nastavit buď na datovém zdroji, nebo na jednotlivých obrázcích za každým datovým zdrojem, které mají změnit, kdy a jak jsou tyto prostředky zobrazeny.

   **Schéma manifestu obrázku**

   Kompletní manifest obrázku vypadá takto:

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

 Jako pomůcku pro čitelnost a údržbu může manifest obrázku použít symboly pro hodnoty atributů. Symboly jsou definovány takto:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Dílčím**|**Definice**|
|Import|Importuje symboly daného souboru manifestu pro použití v aktuálním manifestu.|
|Identifikátor GUID|Symbol představuje identifikátor GUID a musí odpovídat formátování GUID.|
|ID|Symbol představuje ID a musí být nezáporné celé číslo.|
|Řetězec|Symbol představuje libovolnou hodnotu řetězce.|

 Symboly rozlišují malá a velká písmena a odkazují se na něj pomocí syntaxe $(název symbolu):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Některé symboly jsou předdefinovány pro všechny manifesty. Ty lze použít v uri \<atribut zdroj \<> nebo import> prvek referenční cesty v místním počítači.

|||
|-|-|
|**Symbol**|**Popis**|
|CommonProgramFiles|Hodnota proměnné prostředí %CommonProgramFiles%|
|Místní AppData|Hodnota proměnné prostředí %LocalAppData%|
|Složka manifestu|Složka obsahující soubor manifestu|
|Mydocuments|Úplná cesta ke složce Dokumenty aktuálního uživatele|
|ProgramFiles|Hodnota proměnné prostředí %ProgramFiles%|
|Systém|Složka Windows\System32|
|Windir|Hodnota proměnné prostředí %WinDir%|

 **Image**

 Prvek \<Image> definuje obraz, na který lze odkazovat pomocí zástupného prvku. Identifikátor GUID a ID dohromady tvoří zástupný název obrázku. Zástupné symboly pro obraz musí být jedinečné v celé knihovně obrázků. Pokud více než jeden obrázek má daný zástupný název, první, který se setkal při vytváření knihovny je ten, který je zachován.

 Musí obsahovat alespoň jeden zdroj. Přestože velikostneutrální zdroje poskytne nejlepší výsledky v široké škále velikostí, nejsou vyžadovány. Pokud je služba požádána o obrázek o \<velikosti, která není definována v elementu Image> a neexistuje žádný zdroj neutrální velikost, služba zvolí zdroj pro nejlepší velikost a škáluje jej na požadovanou velikost.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Atribut**|**Definice**|
|Identifikátor GUID|[Povinné] Část guid zástupného symbolu obrázku|
|ID|[Povinné] ID část zástupného symbolu obrázku|
|AllowColorInversion|[Volitelné, výchozí hodnota true] Označuje, zda obraz může mít své barvy programově obrácené při použití na tmavém pozadí.|

 **Zdroj**

 Element \<Zdroj> definuje jeden zdrojový datový zdroj obrazu (XAML a PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Atribut**|**Definice**|
|Uri|[Povinné] Identifikátor URI, který definuje, odkud lze obrázek načíst. Může to být jedna z následujících možností:<br /><br /> - Identifikátor [URI balíčku](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) používající application:/// autoritu<br /><br /> - Absolutní odkaz na zdroj komponenty<br /><br /> - Cesta k souboru obsahujícímu nativní prostředek|
|Pozadí|[Nepovinné] Označuje, co na druhu pozadí zdroj je určen k použití.<br /><br /> Může to být jedna z následujících možností:<br /><br /> - *Světlo*: Zdroj lze použít na světlém pozadí.<br /><br /> - *Tmavý*: Zdroj lze použít na tmavém pozadí.<br /><br /> - *HighContrast*: Zdroj lze použít na libovolném pozadí v režimu vysoký kontrast.<br /><br /> - *HighContrastLight*: Zdroj lze použít na světlém pozadí v režimu vysokého kontrastu.<br /><br /> -*HighContrastDark*: Zdroj lze použít na tmavém pozadí v režimu vysoký kontrast.<br /><br /> Pokud pozadí **atribut** je vynechán, zdroj lze použít na libovolném pozadí.<br /><br /> Pokud **pozadí** je *světlo*, *tmavý*, *HighContrastLight*nebo *HighContrastDark*, barvy zdroje nejsou nikdy obrácené. Pokud **pozadí** je vynechánnebo nastavena na *HighContrast*, inverze zdroje barvy je řízen a **image AllowColorInversion** atribut.|

 Element \<Source> může mít přesně jeden z následujících volitelných podelementů:

||||
|-|-|-|
|**Element**|**Atributy (vše povinné)**|**Definice**|
|\<Velikost>|Hodnota|Zdroj bude použit pro obrázky dané velikosti (v jednotkách zařízení). Obrázek bude čtvercový.|
|\<> rozsahu velikosti|MinSize, MaxVelikost|Zdroj bude použit pro obrázky z MinSize na MaxSize (v jednotkách zařízení) včetně. Obrázek bude čtvercový.|
|\<Kóty>|Šířka, Výška|Zdroj bude použit pro obrázky dané šířky a výšky (v jednotkách zařízení).|
|\<> rozměrů|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Zdroj bude použit pro obrázky od minimální šířky/výšky do maximální šířky/výšky (v jednotkách zařízení) včetně.|

 Element \<Source> může mít \<také volitelný podelement NativeResource \<>, který definuje zdrojový>, který je načten z nativního sestavení, nikoli ze spravovaného sestavení.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Atribut**|**Definice**|
|Typ|[Povinné] Typ nativního prostředku, buď XAML nebo PNG|
|ID|[Povinné] Část ID celého čísla nativního prostředku|

 **Imagelist**

 ImageList \<> prvek definuje kolekci obrázků, které mohou být vráceny v jednom proužku. Pás je postaven na vyžádání, podle potřeby.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Atribut**|**Definice**|
|Identifikátor GUID|[Povinné] Část guid zástupného symbolu obrázku|
|ID|[Povinné] ID část zástupného symbolu obrázku|
|Externí|[Volitelné, výchozí false] Označuje, zda zástupný název obrázku odkazuje na obrázek v aktuálním manifestu.|

 Zástupný název pro obsažený obraz nemusí odkazovat na obrázek definovaný v aktuálním manifestu. Pokud obsažený obrázek nelze v knihovně obrázků najít, bude na jeho místě použit prázdný zástupný obrázek.

## <a name="how-to-use-the-tool"></a>Jak nástroj používat
 **Ověření vlastního manifestu obrázku**

 Chcete-li vytvořit vlastní manifest, doporučujeme použít nástroj ManifestFromResources k automatickému generování manifestu. Chcete-li ověřit vlastní manifest, spusťte Prohlížeč knihovny obrázků a vyberte soubor > nastavit cesty... otevřete dialogové okno Adresáře hledání. Nástroj bude používat adresáře vyhledávání k načtení manifestů obrázků, ale bude také používat je k nalezení .dll soubory, které obsahují obrázky v manifestu, takže nezapomeňte zahrnout jak manifest a DLL adresáře v tomto dialogu.

 ![Hledání prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-search.png "Hledání prohlížeče knihovny obrázků")

 Chcete-li vyhledat manifesty a odpovídající knihovny DLL, klepněte na tlačítko **Přidat...** a vyberte nové adresáře hledání. Nástroj si tyto vyhledávací adresáře zapamatuje a lze je zapnout nebo vypnout zaškrtnutím nebo zrušením zaškrtnutí adresáře.

 Ve výchozím nastavení se nástroj pokusí najít instalační adresář sady Visual Studio a přidat tyto adresáře do seznamu adresářů hledání. Adresáře, které nástroj nenajde, můžete přidat ručně.

 Po načtení všech manifestů lze nástroj použít k přepínání barev **pozadí,** **DPI**, **vysokého kontrastu**nebo **šedivého měřítka** pro obrazy, aby uživatel mohl vizuálně zkontrolovat datové zdroje obrázků a ověřit, zda jsou vykreslovány správně pro různá nastavení.

 ![Pozadí prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-background.png "Pozadí prohlížeče knihovny obrázků")

 Barvu pozadí lze nastavit na světlo, tmavou nebo vlastní hodnotu. Výběrem možnosti "Vlastní barva" se otevře dialogové okno výběru barev a přidáte tuto vlastní barvu do spodní části pole se seznamem pozadí pro pozdější snadné vyvolání.

 ![Vlastní barva prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-custom-color.png "Vlastní barva prohlížeče knihovny obrázků")

 Výběrem zástupného panelu obrázku se zobrazí informace o každém skutečném obrázku za tímto zástupným jménem v podokně Podrobnosti obrazu vpravo. Podokno také umožňuje uživatelům kopírovat zástupný název podle názvu nebo nezpracovaná hodnota GUID:ID.

 ![Podrobnosti obrázku Prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-image-details.png "Podrobnosti obrázku Prohlížeče knihovny obrázků")

 Informace zobrazené pro každý zdroj obrazu zahrnují, na jakém pozadí se má zobrazit, zda může být tematický nebo podporuje vysoký kontrast, jaké velikosti je platný nebo zda je neutrální a zda obrázek pochází z nativního sestavení.

 ![Prohlížeč knihovny obrázků může téma](../../extensibility/internals/media/image-library-viewer-can-theme.png "Prohlížeč knihovny obrázků může téma")

 Při ověřování manifestu bitové kopie doporučujeme nasadit seznam a obrazovou dll v jejich reálných umístěních. Tím ověříte, že všechny relativní cesty fungují správně a že knihovna obrázků může najít a načíst knihovnu DLL manifestu a obrázku.

 **Hledání katalogu obrázků KnownMonikers**

 Chcete-li lépe odpovídat visual studio styling, rozšíření Sady Visual Studio můžete použít obrázky v katalogu obrázků Visual Studio spíše než vytváření a používání vlastní. To má tu výhodu, že není nutné udržovat tyto bitové kopie a zaručuje, že obraz bude mít obrázek s vysokým DPI zálohování, takže by měl vypadat správně ve všech nastavení dpi, které podporuje Visual Studio.

 Prohlížeč knihovny obrázků umožňuje prohledávat manifest tak, aby uživatel mohl najít zástupný název, který představuje datový zdroj obrázku, a použít tento zástupný název v kódu. Chcete-li vyhledat obrázky, zadejte do vyhledávacího pole požadovaný hledaný výraz a stiskněte Enter. Stavový řádek v dolní části zobrazí, kolik shod bylo nalezeno z celkového počtu obrázků ve všech manifestech.

 ![Prohlížeč knihovny obrázků, filtr](../../extensibility/internals/media/image-library-viewer-filter.png "Prohlížeč knihovny obrázků, filtr")

 Při hledání zástupných názvů obrázků v existujících manifestech doporučujeme vyhledat a používat pouze zástupné názvy katalogu obrázků visual studia, jiné záměrně veřejně přístupné zástupné názvy nebo vlastní zástupné názvy. Pokud používáte neveřejné zástupné názvy, vlastní ui může být přerušeno nebo jeho obrázky změnit neočekávaným způsobem, pokud nebo když tyto neveřejné zástupné názvy a obrázky jsou změněny nebo aktualizovány.

 Kromě toho je možné vyhledávání podle GUID. Tento typ hledání je užitečné pro filtrování seznamu do jednoho manifestu nebo jeden pododdíl manifestu, pokud tento manifest obsahuje více identifikátorů GUID.

 ![Identifikátor GUID filtru prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Identifikátor GUID filtru prohlížeče knihovny obrázků")

 A konečně, vyhledávání podle ID je možné také.

 ![ID filtru prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-filter-id.png "ID filtru prohlížeče knihovny obrázků")

## <a name="notes"></a>Poznámky

- Ve výchozím nastavení bude nástroj vytáhnout v několika manifestů bitových obrázků v adresáři instalace sady Visual Studio. Jediný, který má veřejně spotřební zástupné názvy je **Microsoft.VisualStudio.ImageCatalog** manifest. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 **(nepřepisovat** tento identifikátor GUID ve vlastním manifestu) Typ: KnownMonikers

- Nástroj se pokusí při spuštění načíst všechny image manifesty, které najde, takže může trvat několik sekund, než se aplikace skutečně zobrazí. Může být také pomalé nebo neodpovídá při načítání manifestů.

## <a name="sample-output"></a>Vzorový výstup
 Tento nástroj negeneruje žádný výstup.
