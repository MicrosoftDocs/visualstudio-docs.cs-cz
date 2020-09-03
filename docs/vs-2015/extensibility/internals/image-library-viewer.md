---
title: Prohlížeč knihovny obrázků | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f6423c569fd1909539de9460ab3dcde0bcf753c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532025"
---
# <a name="image-library-viewer"></a>Prohlížeč knihovny obrázků
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nástroj Prohlížeč knihovny obrázků sady Visual Studio může načíst a vyhledat manifesty obrázků a umožnit tak uživateli manipulovat stejným způsobem jako v aplikaci Visual Studio. Uživatel může měnit pozadí, velikosti, DPI, vysoký kontrast a další nastavení. Nástroj také zobrazí informace o načítání pro každý manifest obrázku a zobrazí informace o zdroji pro každý obrázek v manifestu obrázku. Tento nástroj je užitečný pro:  
  
1. Diagnostikování chyb  
  
2. Zajištění správného nastavení atributů v manifestech vlastních imagí  
  
3. Hledání imagí v katalogu imagí sady Visual Studio tak, aby rozšíření sady Visual Studio mohlo používat obrázky, které odpovídají stylu sady Visual Studio  
  
   ![Prohlížeč knihovny obrázků Hero](../../extensibility/internals/media/image-library-viewer-hero.png "Prohlížeč knihovny obrázků Hero")  
  
   **Moniker bitové kopie**  
  
   Moniker obrázku (neboli moniker pro krátký) je identifikátor GUID: ID, který jedinečně identifikuje prostředek obrázku nebo prostředek seznamu obrázků v knihovně imagí.  
  
   **Image – soubory manifestu**  
  
   Soubory manifestu obrázků (. imagemanifest) jsou soubory XML, které definují sadu prostředků obrázků, monikery, které tyto prostředky představují, a skutečný obrázek nebo obrázky, které představují jednotlivé assety. Manifesty obrázků mohou definovat samostatné obrázky nebo seznamy obrázků pro podporu starší verze uživatelského rozhraní. Kromě toho existují atributy, které lze nastavit buď na Asset, nebo na jednotlivých obrázcích za každým Assetem, aby se změnily, kdy a jak se tyto prostředky zobrazují.  
  
   **Schéma manifestu obrázku**  
  
   Úplný manifest obrázku vypadá takto:  
  
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
  
 V rámci podpory čitelnosti a údržby může manifest obrázku používat symboly pro hodnoty atributů. Symboly jsou definovány takto:  
  
```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  
  
|**Dílčí element**|**Definition**|  
|-|-|  
|Import|Importuje symboly daného souboru manifestu pro použití v aktuálním manifestu.|  
|Identifikátor GUID|Symbol představuje identifikátor GUID a musí odpovídat formátování identifikátoru GUID.|  
|ID|Symbol představuje ID a musí být nezáporné celé číslo.|  
|Řetězec|Symbol představuje libovolnou řetězcovou hodnotu.|  
  
 V symbolech rozlišuje velká a malá písmena a jsou odkazovány pomocí syntaxe $ (symbol-Name):  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Některé symboly jsou předdefinované pro všechny manifesty. Ty lze použít v atributu identifikátoru URI \<Source> \<Import> prvku nebo na odkazování cest v místním počítači.  
  
|**Písmeno**|**Popis**|  
|-|-|  
|CommonProgramFiles|Hodnota proměnné prostředí% CommonProgramFiles%|  
|LocalAppData|Hodnota proměnné prostředí% LocalAppData%|  
|ManifestFolder|Složka obsahující soubor manifestu|  
|Dokumenty|Úplná cesta ke složce dokumenty aktuálního uživatele|  
|ProgramFiles|Hodnota proměnné prostředí% ProgramFiles%|  
|Systém|Složka Windows\System32|  
|Adresář|Hodnota proměnné prostředí% WinDir%|  
  
 **Image**  
  
 \<Image>Prvek definuje obrázek, na který může odkazovat moniker. Identifikátor GUID a ID, které se přijímají společně tvoří moniker bitové kopie. Moniker obrázku musí být v celé knihovně imagí jedinečný. Pokud má více než jeden obrázek daný moniker, při sestavování knihovny je ten, který se zachovává.  
  
 Musí obsahovat alespoň jeden zdroj. I když zdroje s neutrální velikostí poskytnou nejlepší výsledky napříč širokou škálou velikostí, nejsou nutné. Pokud je služba požádána o obrázek velikosti, která není definována v \<Image> elementu a neexistuje žádný neutrální zdroj, služba vybere zdroj, který je pro konkrétní velikost specifický, a bude ho škálovat na požadovanou velikost.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
    
|**Atribut**|**Definition**|  
|-|-|
|Identifikátor GUID|Požadovanou Část GUID monikeru image|  
|ID|Požadovanou Část ID monikeru bitové kopie|  
|AllowColorInversion|[Volitelné, výchozí hodnota true] Určuje, zda může být barva obrázku při použití na tmavém pozadí převrácena prostřednictvím kódu programu.|  
  
 **Zdroj**  
  
 \<Source>Prvek definuje jeden prostředek zdroje obrázku (XAML a PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|**Atribut**|**Definition**|  
|-|-|  
|Identifikátor URI|Požadovanou Identifikátor URI, který definuje, ze kterého může být obrázek načten. Může to být jedna z následujících:<br /><br /> – [Identifikátor URI balíčku](https://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx) pomocí autority Application:///<br /><br /> – Odkaz na prostředek absolutní součásti<br /><br /> – Cesta k souboru, který obsahuje nativní prostředek|  
|Pozadí|Volitelné Označuje, jaký typ pozadí má zdroj použít.<br /><br /> Může to být jedna z následujících:<br /><br /> - *Světlý*: zdroj lze použít na světlém pozadí.<br /><br /> - *Tmavě*: zdroj lze použít na tmavém pozadí.<br /><br /> - *HighContrast*: zdroj lze použít na jakémkoli pozadí v režimu Vysoký kontrast.<br /><br /> - *HighContrastLight*: zdroj lze použít na světlém pozadí v režimu Vysoký kontrast.<br /><br /> -*HighContrastDark*: zdroj lze použít na tmavém pozadí v režimu Vysoký kontrast.<br /><br /> Pokud je atribut **Background** vynechán, lze zdroj použít na jakémkoli pozadí.<br /><br /> Pokud **Background** je pozadí *světlé*, *tmavé*, *HighContrastLight*nebo *HighContrastDark*, barvy zdroje se nikdy nezmění. Pokud je **pozadí** vynecháno nebo je nastaveno na *HighContrast*, je inverze barev zdroje řízena atributem **AllowColorInversion** obrázku.|  
  
 \<Source>Element může mít přesně jeden z následujících volitelných dílčích elementů:  
  
|**Prvek**|**Atributy (všechny povinné)**|**Definition**|  
|-|-|-|  
|\<Size>|Hodnota|Zdroj se použije pro obrázky dané velikosti (v jednotkách zařízení). Obrázek bude čtvercový.|  
|\<SizeRange>|MinSize, MaxSize|Zdroj bude použit pro obrázky z MinSize do MaxSize (v jednotkách zařízení) včetně. Obrázek bude čtvercový.|  
|\<Dimensions>|Šířka, Výška|Zdroj se použije pro obrázky zadané šířky a výšky (v jednotkách zařízení).|  
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Zdroj bude použit pro obrázky z minimální šířky a výšky až po maximální šířku a výšku (v jednotkách zařízení) včetně.|  
  
 \<Source>Element může mít také volitelný \<NativeResource> dílčí element, který definuje \<Source> , který je načten z nativního sestavení namísto spravovaného sestavení.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|**Atribut**|**Definition**|  
|-|-|  
|Typ|Požadovanou Typ nativního prostředku, buď XAML, nebo PNG|  
|ID|Požadovanou Část celého čísla ID nativního prostředku|  
  
 **Obrázků**  
  
 \<ImageList>Prvek definuje kolekci obrázků, které mohou být vráceny v jednom pruhu. Pruh je podle potřeby založený na vyžádání.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|**Atribut**|**Definition**|  
|-|-|  
|Identifikátor GUID|Požadovanou Část GUID monikeru image|  
|ID|Požadovanou Část ID monikeru bitové kopie|  
|Externí|[Volitelné, výchozí hodnota false] Určuje, zda moniker image odkazuje na obrázek v aktuálním manifestu.|  
  
 Moniker pro obsažený obrázek nemusí odkazovat na obrázek definovaný v aktuálním manifestu. Pokud v knihovně obrázků není nalezen obsažený obrázek, bude na svém místě použit prázdný zástupný obrázek.  
  
## <a name="how-to-use-the-tool"></a>Jak používat nástroj  
 **Ověření manifestu vlastního obrázku**  
  
 Chcete-li vytvořit vlastní manifest, doporučujeme použít nástroj ManifestFromResources k vygenerování manifestu. Chcete-li ověřit vlastní manifest, spusťte prohlížeč knihovny obrázků a vyberte soubor > nastavit cesty... Otevřete dialogové okno Hledat adresáře. Nástroj bude používat adresáře hledání k načtení manifestů obrázků, ale bude ho také používat k nalezení souborů. dll, které obsahují obrázky v manifestu, takže nezapomeňte do tohoto dialogu zahrnout adresáře manifest i DLL.  
  
 ![Hledání v prohlížeči knihovny obrázků](../../extensibility/internals/media/image-library-viewer-search.png "Hledání v prohlížeči knihovny obrázků")  
  
 Klikněte na tlačítko **Přidat...** Chcete-li vybrat nové adresáře hledání pro hledání manifestů a jejich odpovídajících knihoven DLL. Tento nástroj si tyto adresáře hledání zapamatuje a bude možné ho zapnout nebo vypnout zaškrtnutím nebo zrušením zaškrtnutí tohoto adresáře.  
  
 Ve výchozím nastavení se nástroj pokusí najít instalační adresář sady Visual Studio a přidat tyto adresáře do seznamu adresáře hledání. Můžete ručně přidat adresáře, které nástroj nenalezne.  
  
 Po načtení všech manifestů se dá nástroj použít k přepnutí barev **pozadí** , **rozlišení DPI**, **vysokého kontrastu**nebo **grayscaling** obrázků, aby uživatel mohl vizuálně kontrolovat prostředky imagí, aby ověřil, že jsou vygenerovány správně pro různá nastavení.  
  
 ![Pozadí prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-background.png "Pozadí prohlížeče knihovny obrázků")  
  
 Barva pozadí může být nastavena na hodnotu světlá, tmavě nebo vlastní. Když vyberete vlastní barvu, otevře se dialogové okno pro výběr barvy a tato vlastní barva se přidá do dolní části pole se seznamem na pozadí pro snadné odvolání později.  
  
 ![Vlastní barva prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-custom-color.png "Vlastní barva prohlížeče knihovny obrázků")  
  
 Po výběru monikeru image se zobrazí informace pro každý skutečný obraz na daném monikeru v podokně podrobností obrázku na pravé straně. Podokno také umožňuje uživatelům kopírovat moniker podle názvu nebo pomocí nepůvodní hodnoty GUID: ID.  
  
 ![Podrobnosti obrázku prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-image-details.png "Podrobnosti obrázku prohlížeče knihovny obrázků")  
  
 Informace zobrazené pro každý zdroj obrázku obsahují typ pozadí, na kterém se má zobrazit, zda může být motivem nebo podporuje Vysoký kontrast, jaké velikosti jsou platné pro nebo zda je velikost neutrální a zda je obrázek z nativního sestavení.  
  
 ![Prohlížeč knihovny obrázků může motivovat](../../extensibility/internals/media/image-library-viewer-can-theme.png "Prohlížeč knihovny obrázků může motivovat")  
  
 Při ověřování manifestu bitové kopie doporučujeme nasadit manifest a image DLL v umístěních reálného světa. Tím ověříte, zda všechny relativní cesty fungují správně a zda knihovna imagí může najít a načíst manifest a image DLL.  
  
 **Hledání katalogu imagí KnownMonikers**  
  
 Aby lépe odpovídaly stylům sady Visual Studio, může rozšíření sady Visual Studio používat obrázky v katalogu imagí sady Visual Studio, nikoli vytvářet a používat vlastní. To má za následek, že tyto image nemusíte uchovávat a zaručuje, že obrázek bude mít image s vysokým rozlišením DPI, takže by měl vypadat správně ve všech nastaveních DPI, které podporuje Visual Studio.  
  
 Prohlížeč knihovny imagí umožňuje vyhledat manifest, aby uživatel mohl najít moniker reprezentující prostředek obrázku a použít tento moniker v kódu. Chcete-li vyhledat obrázky, zadejte požadovaný hledaný termín do vyhledávacího pole a stiskněte klávesu ENTER. Na stavovém řádku v dolní části se zobrazí počet nalezených shod z celkového počtu imagí ve všech manifestech.  
  
 ![Filtr prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-filter.png "Filtr prohlížeče knihovny obrázků")  
  
 Při hledání monikerů imagí v existujících manifestech doporučujeme vyhledat a použít pouze monikery katalogu imagí sady Visual Studio, jiné záměrně veřejně přístupné monikery nebo vlastní monikery. Pokud používáte monikery NonPublic, může být vlastní uživatelské rozhraní přerušeno nebo se jeho image změnily neočekávaným způsobem, pokud nebo dojde ke změně nebo aktualizaci těchto zástupných názvů a imagí NonPublic.  
  
 Kromě toho je možné hledat podle identifikátoru GUID. Tento typ hledání je vhodný pro filtrování dolů v seznamu do jednoho manifestu nebo jednoho dílčího oddílu manifestu, pokud tento manifest obsahuje více identifikátorů GUID.  
  
 ![Identifikátor GUID filtru prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Identifikátor GUID filtru prohlížeče knihovny obrázků")  
  
 Nakonec je možné také prohledávat podle ID.  
  
 ![ID filtru prohlížeče knihovny obrázků](../../extensibility/internals/media/image-library-viewer-filter-id.png "ID filtru prohlížeče knihovny obrázků")  
  
## <a name="notes"></a>Poznámky  
  
- Ve výchozím nastavení se nástroj vyžádá v několika manifestech obrázků, které jsou k dispozici v instalačním adresáři sady Visual Studio. Jediným názvem, který má veřejné přístupnosti, je manifest **Microsoft. VisualStudio. ImageCatalog** . GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 ( **Nepřepisovat** tento identifikátor GUID ve vlastním manifestu): KnownMonikers  
  
- Nástroj se při spuštění pokusí načíst všechny manifesty obrázků, které najde, takže může trvat několik sekund, než se aplikace skutečně zobrazí. Při načítání manifestů může být také pomalé nebo nereagující.  
  
## <a name="sample-output"></a>Vzorový výstup  
 Tento nástroj negeneruje žádný výstup.
