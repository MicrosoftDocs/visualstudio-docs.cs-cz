---
title: Globalizace a lokalizace řešení pro Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ade59e757778ac7858732f5bf9880b9f88eacd69
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39567469"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Globalizace a lokalizace řešení pro Excel
  Tato část obsahuje informace o důležité informace pro řešení Microsoft Office Excel, která se spustí na počítačích, které mají jiné než anglické jazykové nastavení pro Windows. Většinu aspektů globalizace a lokalizace řešení pro Microsoft Office jsou stejné jako dojde při vytvoření jiných typů řešení s využitím sady Visual Studio. Obecné informace najdete v tématu [Globalize a lokalizace aplikací](/visualstudio/ide/globalizing-and-localizing-applications).  
  
 Ve výchozím nastavení hostitelské ovládací prvky v aplikaci Microsoft Office Excel práce správně v regionální nastavení Windows, tak dlouho, dokud všechna data, která je předána ani s nimi manipulovat, pomocí spravovaného kódu je naformátována pomocí formátování Angličtina (Spojené státy). V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], toto chování je řízen modulem common language runtime (CLR).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="format-data-in-excel-with-various-regional-settings"></a>Formátování dat v aplikaci Excel s různá místní nastavení  
 Je nutné naformátovat všechna data, která obsahuje citlivé na národní prostředí formátování, jako je například kalendářní data a Měna, ve formátu data Angličtina (Spojené státy) (národní prostředí ID 1033) před předávat do aplikace Microsoft Office Excel nebo číst data z kódu v projektu Office.  
  
 Ve výchozím nastavení při vývoji řešení pro Office v sadě Visual Studio, objektový model aplikace Excel očekává, že formátování dat ID 1033 národního prostředí (to se také nazývá zamykání objektový model pro národní prostředí ID 1033). Toto chování odpovídá způsobu, jakým funguje Visual Basic for Applications. Toto chování však můžete upravit ve vašich řešeních pro Office.  
  
### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>Vysvětlení, jak objektovému modelu Excelu. vždy očekává, že ID 1033 národního prostředí  
 Ve výchozím nastavení řešení pro systém Office, které vytvoříte pomocí sady Visual Studio nevztahují na nastavení národního prostředí koncového uživatele a vždy se chovají jako by národní prostředí je angličtina (Spojené státy). Například, pokud je získání nebo nastavení <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> vlastnosti v aplikaci Excel, data musí být ve formátu tak, jak očekává, že ID národního prostředí 1033. Pokud používáte formát různých dat, může se zobrazit neočekávané výsledky.  
  
 I když použijete formát Angličtina (Spojené státy) pro data, která je předána ani s nimi manipulovat spravovaným kódem, aplikace Excel interpretuje a zobrazí data správně podle nastavení národního prostředí koncového uživatele. Aplikace Excel můžete naformátovat data správně, protože spravovaný kód předá národní prostředí ID 1033 spolu s daty, což znamená, že data jsou v angličtině (USA) formátu a proto musí být přeformátovali tak, aby odpovídaly nastavení národního prostředí uživatele.  
  
 Například pokud koncoví uživatelé mají svá místní nastavení nastavit s národním prostředím němčina (Německo), očekávané datum 29. června, 2005, má být formátováno tímto způsobem: 29.06.2005. Nicméně pokud vaše řešení předá data do aplikace Excel jako řetězec, je nutné naformátovat datum podle používaného Angličtina (Spojené státy) formát: 6/29/2005. Pokud buňky je formátován jako buňku data, aplikace Excel se zobrazí datum ve formátu němčina (Německo).  
  
### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>Předání dalších ID národního prostředí k objektovému modelu Excelu.  
 Common language runtime (CLR) automaticky předá národní prostředí ID 1033 pro všechny metody a vlastnosti v modelu objektů aplikace Excel, které přijímají data citlivé na národní prostředí. Neexistuje žádný způsob, jak změnit toto chování automaticky pro všechna volání do objektového modelu. Ale můžete předat ID jiné národní prostředí pro konkrétní metody pomocí <xref:System.Type.InvokeMember%2A> k volání metody a předáním ID národního prostředí pro *jazykovou verzi* parametru metody.  
  
## <a name="localize-document-text"></a>Lokalizace textového dokumentu  
 Dokument, šablonu nebo sešitu ve vašem projektu nejspíš obsahuje statický text, který musí být lokalizovaný odděleně od sestavení a další spravované prostředky. Jednoduchý způsob, jak to provést je vytvořit kopii dokumentu a překládat text pomocí aplikace Microsoft Office Word nebo Microsoft Office Excel. Tento proces funguje i když neprovedete žádné změny kódu, protože lze propojit libovolný počet dokumentů do stejného sestavení.  
  
 Stále musíte zkontrolovat, že libovolné části kódu, který komunikuje s textem dokument i nadále jazyk textu, a to této záložky, pojmenované oblasti, a další pole zobrazení zvládnutí přeformátování dokument Office, který bylo nutné Upravte jinou délku gramatiky a text. Pro šablony dokumentů, které obsahují poměrně málo text můžete chtít zvážit ukládání textu do souborů prostředků a potom načítání textu za běhu.  
  
### <a name="text-direction"></a>Směr textu  
 V aplikaci Excel můžete nastavit vlastnost listu pro vykreslení textu zprava doleva. Hostování ovládacích prvků nebo libovolný ovládací prvek, který má `RightToLeft` vlastnost, která se přikládá návrháře automaticky odpovídat následujícímu nastavení za běhu. Není k dispozici nastavení dokument pro obousměrný text (stačí změnit váš zarovnání textu), takže ovládací prvky nelze mapovat na toto nastavení. Místo toho je nutné nastavit zarovnání textu pro každý ovládací prvek. Je možné napsat kód, který provede všechny ovládací prvky a vynuťte jejich vykreslení textu zprava doleva.  
  
### <a name="change-culture"></a>Změna jazykové verze  
 Přizpůsobení na úrovni dokumentu kódu obvykle sdílí hlavního vlákna uživatelského rozhraní aplikace Excel, takže všechno ostatní, na kterém běží v daném vláknu; ovlivní všechny změny provedené u jazykové verzi vlákna změny se neomezuje na vašem vlastním přizpůsobení.  
  
 Ovládací prvky Windows Forms jsou inicializovány před úrovni aplikace doplňků VSTO jsou spouštěny hostitelskou aplikaci. V těchto situacích by měl změnit jazykovou verzi před nastavením ovládacích prvků uživatelského rozhraní.  
  
## <a name="install-the-language-packs"></a>Instalace jazykové sady  
 Pokud máte jiné než anglické jazykové nastavení pro Windows, můžete nainstalovat [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jazykových sad zobrazíte [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zprávy ve stejném jazyce jako Windows. Pokud koncové uživatele, spusťte řešení pomocí jiné než anglické jazykové nastavení pro Windows, musí mít správné jazykovou sadu pro zobrazení zpráv modulu runtime ve stejném jazyce jako Windows. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Jazykové sady jsou k dispozici [webu služby Stažení softwaru](http://www.microsoft.com/downloads).  
  
 Kromě toho jsou nezbytné pro zprávy ClickOnce redistributable jazykové sady rozhraní .NET Framework. Jazykové sady rozhraní .NET Framework jsou k dispozici [webu služby Stažení softwaru](http://www.microsoft.com/downloads).  
  
## <a name="regional-settings-and-excel-com-calls"></a>Místní nastavení a volání COM aplikace Excel  
 Pokaždé, když se spravovaný klient volá metodu na objekt modelu COM a nepotřebuje předávat informace specifické jazykové verze, dělá to pomocí <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (národní prostředí), který odpovídá aktuální národní prostředí pro vlákno. Aktuální národní prostředí pro vlákno se ve výchozím nastavení dědí z místní nastavení uživatele. Ale při volání do objektového modelu aplikace Excel z aplikace Excel řešení vytvořené pomocí nástroje pro vývoj pro Office v sadě Visual Studio, formát dat Angličtina (Spojené státy) (ID 1033 národní prostředí) je předán k objektovému modelu Excelu automaticky. Je nutné naformátovat všechna data, která má formátování citlivé na národní prostředí, jako je například kalendářní data a Měna, ve formátu Angličtina (Spojené státy) data před předávat do aplikace Microsoft Office Excel nebo číst data z vašeho kódu projektu.  
  
## <a name="considerations-for-storing-data"></a>Důležité informace pro ukládání dat.  
 Chcete-li zajistit, aby vaše data správně interpretován a zobrazen, měli byste taky zvážit, že může dojít k problémům při aplikace je ukládání dat, jako jsou vzorce listu aplikace Excel, v řetězcové literály (pevně zakódované) místo v silně typované objekty. Měli byste použít data, která je ve formátu za předpokladu, že styl invariantní jazykovou verzi nebo Angličtina (Spojené státy) (LCID hodnotu 1033).  
  
### <a name="applications-that-use-string-literals"></a>Aplikace, které používají řetězcové literály  
 Možné hodnoty, které mohou být pevně zakódované zahrnují date – literály, které jsou napsané ve formátu Angličtina (Spojené státy) a vzorce listu aplikace Excel, které obsahují lokalizované názvy. Další možností, může být pevně zakódované řetězce, který obsahuje čísla, jako je například "1000;" v některých jazykových verzí to je interpretován jako tisíc, ale v jiné jazykové verze, představuje jeden bod nula. Výpočty a porovnání provedené na má nesprávný formát může mít za následek nesprávná data.  
  
 Všechny řetězce v souladu s LCID, který je předán s řetězec interpretován. To může být problém, pokud formát řetězce neodpovídá LCID, který je předán. Při předávání všechna data, pomocí nástroje pro vývoj pro Office v sadě Visual Studio vytvoří řešení pro aplikaci Excel použít 1033 LCID (en US). Aplikace Excel zobrazuje data podle místní nastavení a jazyk uživatelského rozhraní aplikace Excel. Visual Basic for Applications (VBA) také funguje tímto způsobem; řetězce jsou formátovány jako en US a VBA skoro vždycky předá 0 (jazykově neutrální) jako identifikátor LCID. Například následující kód VBA zobrazí správně formátovaná hodnota pro May 12, 2004, v souladu s aktuální nastavení národního prostředí uživatele:  
  
```vb
'VBA  
Application.ActiveCell.Value2 = "05/12/04"  
```  
  
 Stejný kód, při použití v řešení vytvořené pomocí nástroje pro vývoj pro Office v sadě Visual Studio a předat do aplikace Excel prostřednictvím zprostředkovatele komunikace s objekty COM, vytvoří stejné výsledky, když se data formátují ve stylu en US.  
  
 Příklad:  
  
 [!code-vb[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#6)]
 [!code-csharp[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#6)]  
  
 By měl pracovat s daty silného typu místo řetězcové literály, kdykoli je to možné. Například místo ukládání datum v řetězcovém literálu, uložte ho jako <xref:System.Double>, převeďte jej <xref:System.DateTime> objekt pro manipulaci s.  
  
 Následující příklad kódu používá data, které uživatel zadá do buňky A5, uloží ho jako <xref:System.Double>, potom převede jej na <xref:System.DateTime> objektu pro zobrazení v buňce A7. Chcete-li zobrazit datum musí být naformátovaná A7 buňky.  
  
 [!code-vb[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#7)]
 [!code-csharp[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#7)]  
  
### <a name="excel-worksheet-functions"></a>Funkce listu aplikace Excel  
 Názvy funkcí listu jsou přeloženy interně pro většinu jazykové verze aplikace Excel. Z důvodu možných jazyka a modelu COM interop problémy však doporučujeme použít pouze anglické funkce názvy v kódu.  
  
### <a name="applications-that-use-external-data"></a>Aplikace, které používají externích dat  
 Veškerý kód, který otevře nebo jinak používá externí data, jako jsou soubory, které obsahují textový soubor s oddělovači (CSV soubory) exportovat ze starší verze systému, může mít vliv i pokud tyto soubory jsou exportovány všechny formátu kromě en US. Přístup k databázi nemusí být ovlivněno, protože všechny hodnoty musí být v binárním formátu, pokud databáze ukládá data jako řetězce nebo provádí operace, které nepoužívají binární formát. Také pokud je možné vytvářet dotazy SQL pomocí dat z Excelu, potřebujete ověřte, že jsou ve formátu en US, v závislosti na funkci, kterou používáte.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: cílení na vícejazyčné uživatelské rozhraní sady Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  