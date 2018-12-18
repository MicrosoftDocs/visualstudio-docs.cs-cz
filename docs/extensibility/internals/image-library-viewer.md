---
title: Prohlížeč knihovny obrázků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7808c4485a00c080a8a5b260a6472d81bfb7fd44
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816823"
---
# <a name="image-library-viewer"></a>Prohlížeč knihovny obrázků
Nástroj Prohlížeč knihovny obrázků Visual Studio můžete načíst a vyhledávat image manifestů, které uživateli umožňují s nimi manipulovat stejným způsobem, který by sady Visual Studio. Uživatel může změnit na pozadí, velikosti, DPI, vysoký kontrast a další nastavení. Tento nástroj také zobrazuje informace o načítání pro každou manifestu obrázků a zobrazí informace o zdroji pro každý obrázek v manifestu obrázků. Tento nástroj je užitečný pro:  
  
1. Diagnostika chyb  
  
2. Atributy zajistit, že jsou správně nastavené v manifestech vlastní image  
  
3. Vyhledávání obrázků v katalogu obrázků Visual Studio tak, aby rozšíření sady Visual Studio můžete použít Image, které vyhovují stylu sady Visual Studio  
  
   ![Hero prohlížeč knihovny obrázků](../../extensibility/internals/media/image-library-viewer-hero.png "Hero prohlížeč knihovny obrázků")  
  
   **Moniker obrázku.**  
  
   Moniker bitové kopie (nebo moniker short) je GUID:ID pár, který jednoznačně identifikuje prostředek obrázku nebo seznam prostředků obrázků v knihovně obrázků.  
  
   **Soubory manifestu obrázků**  
  
   Soubory manifestu (.imagemanifest) bitové kopie jsou soubory XML, které definují sadu prostředky obrázků, zástupných názvů, které představují tyto prostředky a skutečné bitové kopie nebo bitové kopie, které představují každou asset. Manifesty Image můžete definovat samostatné obrázky nebo bitové kopie jsou uvedené pro stále podporuje starší verze uživatelského rozhraní. Kromě toho jsou atributy, které je možné nastavit na prostředku nebo na jednotlivých obrázků za každý prostředek změnit, kdy a jak tyto prostředky jsou zobrazené.  
  
   **Schéma manifestu obrázků**  
  
   Manifest kompletní obrázek vypadá takto:  
  
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
  
 Jako podporu čitelnost a údržbu, image manifest můžete použít symboly pro hodnoty atributů. Značky jsou definovány takto:  
  
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
|**Dílčí element**|**Definice**|  
|Importovat|Importuje symboly daný soubor manifestu pro použití v aktuální manifestu.|  
|identifikátor GUID|Symbol představuje identifikátor GUID a GUID formátování se musí shodovat.|  
|ID|Symbol představuje ID a musí být nezáporné celé číslo.|  
|String|Symbol představuje libovolný řetězcovou hodnotu.|  
  
 Symboly jsou malá a velká písmena a odkazované pomocí syntaxe $(symbol-name):  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 U všech manifestů jsou předdefinovány některé symboly. Ty je možné použít v atributu identifikátor Uri \<zdroj > nebo \<Import > – element pro cesty odkazů v místním počítači.  
  
|||  
|-|-|  
|**Symbol**|**Popis**|  
|CommonProgramFiles|Hodnota proměnné prostředí % CommonProgramFiles %|  
|LocalAppData|Hodnota proměnné prostředí % LocalAppData %|  
|ManifestFolder|Složku, která obsahuje soubor manifestu|  
|Dokumenty|Úplná cesta ke složce Dokumenty aktuálního uživatele|  
|ProgramFiles|Hodnota proměnné prostředí % ProgramFiles %|  
|Systém|Složky Windows\System32|  
|WinDir|Hodnota proměnné prostředí % WinDir %|  
  
 **Obrázek**  
  
 \<Image > element definuje bitovou kopii, která lze odkazovat pomocí monikeru. Identifikátor GUID a ID, které dohromady tvoří moniker bitové kopie. Moniker bitové kopie musí být jedinečný ve knihovny celého obrázku. Pokud více než jednu image má daný monikeru, došlo při vytváření knihovny k první z nich je ten, který je zachováno.  
  
 Musí obsahovat alespoň jeden zdroj. I když velikost jazykově neutrální zdrojů vám poskytne nejlepší výsledky napříč širokou škálu velikostí, nejsou vyžadovány. Pokud služba se zobrazí výzva o určité imagi velikost není definovaný v \<Image > element a neexistuje žádný zdroj velikost doménově neutrální, služba bude zvolit nejlepší zdroj konkrétní velikosti a škálovat ji na požadovanou velikost.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|identifikátor GUID|[Povinné] Část GUID moniker obrázku.|  
|ID|[Povinné] ID část moniker obrázku.|  
|AllowColorInversion|[Volitelné, výchozí hodnota true] Určuje, jestli obrázek může mít jeho barvy programově obrácený v tmavém pozadí.|  
  
 **Zdroj**  
  
 \<Zdroj > element definuje jediný zdroj zdroj obrázku (XAML a PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|Identifikátor URI|[Povinné] Identifikátor URI, který definuje, kde je možné načíst image z. Může být jeden z následujících akcí:<br /><br /> -A [identifikátory Pack URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) používání aplikace pro: / / / / / autority<br /><br /> Odkaz na prostředek – absolutní komponenty<br /><br /> – Cesta k souboru, který obsahuje nativní prostředky|  
|Pozadí|[Volitelné] Určuje, co na pozadí, který zdroj je určena pro použití typu.<br /><br /> Může být jeden z následujících akcí:<br /><br /> - *Světlý*: zdroj jde použít na světla na pozadí.<br /><br /> - *Tmavě*: zdroj je možné v tmavém pozadí.<br /><br /> - *Funkce Vysoký kontrast*: zdroj jde použít na jakékoli na pozadí v režimu vysokého kontrastu.<br /><br /> - *HighContrastLight*: zdroj je možné na pozadí světla v režimu vysokého kontrastu.<br /><br /> -*HighContrastDark*: zdroj je možné v tmavém pozadí v režimu vysokého kontrastu.<br /><br /> Pokud **pozadí** atribut je vynechán, zdroj je použít na jakékoli pozadí.<br /><br /> Pokud **pozadí** je *světla*, *tmavě*, *HighContrastLight*, nebo *HighContrastDark*, Nikdy se převrátí zdroje barvy. Pokud **pozadí** je vynechán nebo nastaven na *funkce Vysoký kontrast*, inverzi barev zdroji se řídí na obrázku **AllowColorInversion** atribut.|  
  
 A \<zdroj > prvek může mít nastavený právě jeden z následující volitelné dílčí prvky:  
  
||||  
|-|-|-|  
|**Element**|**Atributy (všechny povinné)**|**Definice**|  
|\<Velikost >|Hodnota|Zdroj se použije pro Image dané velikosti (v jednotkách zařízení). Image bude čtvereček.|  
|\<SizeRange >|MinSize MaxSize|Zdroj se použije pro obrázky z MinSize pro parametr MaxSize (v jednotkách zařízení) (včetně). Image bude čtvereček.|  
|\<Dimenze >|Šířka, výška|Zdroj se použije pro Image dané šířky a výšky (v jednotkách zařízení).|  
|\<DimensionRange >|Hodnota MinWidth MinHeight,<br /><br /> MaxWidth MaxHeight|Zdroj se použije pro obrázků ze minimální šířky a výšky na maximální šířku nebo výšku (v jednotkách zařízení) (včetně).|  
  
 A \<zdroj > prvek může mít také volitelný \<NativeResource > dílčího elementu, který definuje \<zdroj >, který je načten z nativní sestavení spíše než spravovaná sestavení.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|Typ|[Povinné] Typ nativního prostředku, XAML nebo PNG|  
|ID|[Povinné] Část celého čísla ID nativní prostředky|  
  
 **Ovládací prvek ImageList**  
  
 \<ImageList > element definuje kolekci imagí, které mohou být vráceny v jedné pruhu. Pruh je postavená na požádání, podle potřeby.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|identifikátor GUID|[Povinné] Část GUID moniker obrázku.|  
|ID|[Povinné] ID část moniker obrázku.|  
|Externí|[Volitelné, výchozí hodnota je false] Určuje, zda moniker bitové kopie odkazuje na obrázek v aktuální manifestu.|  
  
 Moniker pro bitovou kopii obsaženého nemusí odkazovat na image definovaný v manifestu aktuální. Pokud bitovou kopii obsaženého nebyl nalezen v knihovně image, image prázdný zástupný symbol se použije na příslušné místo.  
  
## <a name="how-to-use-the-tool"></a>Jak používat nástroj  
 **Ověřuje se manifest vlastní image**  
  
 K vytvoření vlastního manifestu, doporučujeme vám, že použijete nástroj ManifestFromResources automaticky vygenerovat manifest. Ověření vlastního manifestu, spusťte prohlížeč knihovny obrázků a vyberte soubor > nastavit cesty... Otevřete dialogové okno prohledávaných adresářů. Nástroj používat prohledávaných adresářů pro načtení obrázku manifesty, ale také použije ho je najít soubory .dll, které obsahují obrázky v manifestu, takže nezapomeňte zahrnout manifest i adresáře knihovny DLL v tomto dialogovém okně.  
  
 ![Hledání prohlížeč knihovny obrázků](../../extensibility/internals/media/image-library-viewer-search.png "hledání prohlížeč knihovny obrázků")  
  
 Klikněte na tlačítko **přidat...**  vyberte nový prohledávaných adresářů pro hledání manifestů a jejich odpovídající knihovny DLL. Nástroj bude mějte na paměti tyto prohledávaných adresářů a jejich můžete zapnout nebo vypnout zaškrtnutím nebo zrušením zaškrtnutí adresáře.  
  
 Ve výchozím nastavení nástroj se pokusí najít adresáře instalace sady Visual Studio a přidat tyto adresáře do seznamu hledání adresářů. Můžete ručně přidat adresáře, které nástroj nedokáže najít.  
  
 Jakmile jsou načteny všechny manifesty, nástroj je možné přepínat **pozadí** barvy, **DPI**, **vysoký kontrast –**, nebo **grayscaling** pro Image tak, aby uživatel můžete vizuálně zkoumat prostředky obrázků k ověření, že jsou správně vykreslení pro různá nastavení.  
  
 ![Obrázek pozadí prohlížeč knihovny](../../extensibility/internals/media/image-library-viewer-background.png "pozadí prohlížeč knihovny obrázků")  
  
 Světla, tmavé nebo vlastní hodnotu lze nastavit barvu pozadí. Výběru "vlastní" otevřete dialogové okno Výběr barvy a přidejte vlastní barvy k dolnímu okraji pole se seznamem na pozadí pro jejich snadné odvolání později.  
  
 ![Vlastní barva prohlížeč knihovny obrázků](../../extensibility/internals/media/image-library-viewer-custom-color.png "vlastních barev prohlížeč knihovny obrázků")  
  
 Výběr moniker bitové kopie zobrazí informace o jednotlivých skutečné obrázek pozadí tohoto moniker v podokně podrobností bitové kopie na pravé straně. V podokně také umožňuje uživatelům kopírovat monikeru podle názvu nebo podle GUID:ID nezpracované hodnoty.  
  
 ![Obrázek podrobnosti ke knihovně prohlížeče obraz](../../extensibility/internals/media/image-library-viewer-image-details.png "obrázku podrobnosti ke knihovně Prohlížeč obrázků")  
  
 Informace zobrazené pro každý zdroj obrázku obsahuje jaký druh na pozadí se zobrazí na, zda může být s motivem nebo podporuje vysoký kontrast, jaké velikosti je platný pro nebo určuje, zda je nezávislá na velikost a určuje, zda obrázek pochází z nativní sestavení.  
  
 ![Prohlížeč knihovny obrázků můžete motiv](../../extensibility/internals/media/image-library-viewer-can-theme.png "prohlížeč knihovny obrázků můžete motiv")  
  
 Při ověřování manifestu obrázků, doporučujeme vám, nasadíte manifest a bitové kopie knihovny DLL v jejich skutečné umístění. Tímto se ověří, že všechny relativní cesty, fungují správně a že knihovna obrázků můžete najít a načíst manifest a bitové kopie knihovny DLL.  
  
 **Vyhledávání obrázků katalogu KnownMonikers**  
  
 Tak, aby lépe odpovídaly používání stylů pro Visual Studio, můžete použít rozšíření sady Visual Studio v katalogu obrázků Visual Studio namísto vytváření a používání vlastní Image. To má výhodu není potřeba udržovat těchto imagí a zaručuje, že image bude mít vysokých hodnot DPI základní image, takže by měl vypadat správné všechna nastavení DPI, které podporuje Visual Studio.  
  
 Prohlížeč knihovny obrázků umožňuje manifest, který chcete prohledat tak, aby uživatel může najít moniker, který představuje prostředek obrázku a použít tento zástupný název v kódu. Pro hledání obrázků, do vyhledávacího pole zadejte požadovaný hledaný termín a stiskněte klávesu Enter. Stavový řádek v dolní části se zobrazí, kolik odpovídajících položek nebyly nalezeny mimo celkový počet imagí ve všech manifestů.  
  
 ![Filtr prohlížeč knihovny obrázků](../../extensibility/internals/media/image-library-viewer-filter.png "filtr prohlížeč knihovny obrázků")  
  
 Při hledání obrázků monikery v existujících manifestů, doporučujeme vám, vyhledejte a použijte pouze Visual Studio Image katalogu monikery, jiné záměrně veřejně přístupné monikery nebo vlastní vlastní monikery. Pokud používáte neveřejné monikery, vlastního uživatelského rozhraní nemusí fungovat správně nebo obrázky změnily neočekávaně Pokud nebo při změně nebo aktualizaci těchto neveřejné monikery a obrázky.  
  
 Hledání podle identifikátoru GUID je navíc možné. Tento typ hledání je užitečné pro filtrování seznamu do jednoho manifestu nebo jeden dílčí část objektu manifestu, pokud tento manifest obsahuje více identifikátorů GUID.  
  
 ![Obrázek filtru prohlížeč knihovny GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "obrázek filtru prohlížeč knihovny GUID")  
  
 Nakonec vyhledávání podle ID je možné také.  
  
 ![ID filtr prohlížeč knihovny obrázků](../../extensibility/internals/media/image-library-viewer-filter-id.png "ID filtr prohlížeč knihovny obrázků")  
  
## <a name="notes"></a>Poznámky  
  
-   Ve výchozím nastavení nástroj přetáhne v několika manifesty bitové kopie k dispozici v instalačním adresáři sady Visual Studio. Je pouze jeden, který má veřejně použitelné monikery **Microsoft.VisualStudio.ImageCatalog** manifestu. Identifikátor GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (proveďte **není** přepsat tento identifikátor GUID ve vlastním manifestu) typu: KnownMonikers  
  
-   Nástroj se pokusí při spuštění načíst všechny manifesty bitové kopie, které najde, tak může trvat několik sekund, aplikace bude ve skutečnosti zobrazovat. Také může být pomalý nebo že při načítání manifesty.  
  
## <a name="sample-output"></a>Vzorový výstup  
 Tento nástroj negeneruje žádný výstup.