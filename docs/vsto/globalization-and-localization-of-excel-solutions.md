---
title: Globalizace a lokalizace řešení pro Excel
description: Přečtěte si o speciálních faktorech pro systém Microsoft Office excelových řešení, která se spustí v počítačích, které mají nastavení jiné než anglické verze systému Windows.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fc61f66b2aefaf0e43b1b5af819e0e244feec114
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910308"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Globalizace a lokalizace řešení pro Excel
  Tato část obsahuje informace o speciálních faktorech pro systém Microsoft Office excelových řešení, která se spustí v počítačích, které mají nastavení jiné než anglické verze systému Windows. Většina aspektů globalizace a lokalizace systém Microsoft Office řešení se shoduje s tím, jak se setkáte při vytváření jiných druhů řešení pomocí sady Visual Studio. Obecné informace najdete v tématu [globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md).

 Ve výchozím nastavení ovládací prvky hostování v aplikaci systém Microsoft Office Excel fungují správně v libovolném místním nastavení systému Windows, pokud jsou všechna data, která jsou předána nebo manipulována pomocí spravovaného kódu, formátována pomocí formátování angličtiny (USA). V projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , toto chování je řízeno modulem CLR (Common Language Runtime).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="format-data-in-excel-with-various-regional-settings"></a>Formátování dat v Excelu pomocí různých místních nastavení
 Před tím, než ho předáte do systém Microsoft Office Excelu nebo si můžete přečíst data z kódu v projektu Office, musíte naformátovat všechna data, která mají formátování citlivé na národní prostředí, jako jsou data a měna, pomocí formátu dat anglické verze 1033 (USA).

 Ve výchozím nastavení, když vyvíjíte řešení pro sadu Office v sadě Visual Studio, objektový model aplikace Excel očekává formátování dat ID národního prostředí 1033 (Toto se také označuje jako uzamčení objektového modelu do ID národního prostředí 1033). Toto chování odpovídá způsobu, jakým jazyk Visual Basic for Application funguje. Toto chování však můžete upravit v řešeních pro systém Office.

### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>Vysvětlení způsobu, jakým objektový model aplikace Excel vždycky očekává ID národního prostředí 1033
 Ve výchozím nastavení nejsou řešení Office, která vytvoříte pomocí sady Visual Studio, ovlivněná nastaveními národního prostředí koncového uživatele a vždy se chovají stejně, jako by národní prostředí bylo anglické (USA). Například pokud získáte nebo nastavíte <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> vlastnost v aplikaci Excel, musí být data formátována způsobem, který očekává ID národního prostředí 1033. Pokud používáte jiný formát dat, může docházet k neočekávaným výsledkům.

 I když používáte formát anglické verze (USA) pro data, která jsou předávána nebo zpracována spravovaným kódem, aplikace Excel interpretuje a zobrazuje data správně podle nastavení národního prostředí koncového uživatele. Aplikace Excel může data naformátovat správně, protože spravovaný kód předává ID národního prostředí 1033 společně s daty, což znamená, že data jsou ve formátu anglické verze (USA), a proto je nutné přeformátovat tak, aby odpovídaly nastavení národního prostředí uživatele.

 Například pokud mají koncoví uživatelé své regionální možnosti nastavené na německé národní prostředí (Německo), očekávají datum 29. června 2005, aby se naformátovala takto: 29.06.2005. Pokud však vaše řešení předá data do Excelu jako řetězec, je nutné formátovat datum podle formátu angličtiny (USA): 6/29/2005. Pokud je buňka naformátovaná jako buňka s kalendářními daty, Excel zobrazí datum ve formátu němčina (Německo).

### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>Předat jiným identifikátorům ID národního prostředí do objektového modelu aplikace Excel
 Modul CLR (Common Language Runtime) automaticky předává ID národního prostředí 1033 všem metodám a vlastnostem v modelu objektu aplikace Excel, které přijímají data citlivá na národní prostředí. Neexistuje žádný způsob, jak toto chování automaticky změnit pro všechna volání do objektového modelu. Můžete však předat jiné ID národního prostředí konkrétní metodě pomocí <xref:System.Type.InvokeMember%2A> volání metody a předáním ID národního prostředí do parametru *jazykové verze* metody.

## <a name="localize-document-text"></a>Lokalizace textu dokumentu
 Dokument, šablona nebo sešit v projektu pravděpodobně obsahuje statický text, který musí být lokalizován odděleně od sestavení a dalších spravovaných prostředků. Jednoduchým způsobem, jak to udělat, je vytvořit kopii dokumentu a přeložit text pomocí systém Microsoft Office Wordu nebo systém Microsoft Office Excelu. Tento proces funguje i v případě, že neprovedete žádné změny v kódu, protože libovolný počet dokumentů může být propojen se stejným sestavením.

 Je nutné se ujistit, že všechny části kódu, který komunikuje s textem dokumentu, budou nadále odpovídat jazyku textu a záložky, pojmenované rozsahy a další zobrazovaná pole odpovídají libovolnému přeformátování dokumentu sady Office, který byl nezbytný pro úpravu pro jinou délku gramatiky a textu. Pro šablony dokumentů, které obsahují relativně malý text, je vhodné zvážit ukládání textu do souborů prostředků a následné načtení textu v době běhu.

### <a name="text-direction"></a>Směr textu
 V aplikaci Excel můžete nastavit vlastnost listu pro vykreslení textu zprava doleva. Ovládací prvky hostitele nebo jakýkoli ovládací prvek, který má `RightToLeft` vlastnost umístěnou v návrháři, se automaticky shodují s tímto nastavením v době běhu. Word nemá nastavení dokumentu pro obousměrný text (stačí změnit zarovnání textu), takže ovládací prvky nejde namapovat na toto nastavení. Místo toho je nutné nastavit zarovnání textu pro každý ovládací prvek. Je možné napsat kód, který projde všechny ovládací prvky a vynutí vykreslit text zprava doleva.

### <a name="change-culture"></a>Změnit jazykovou verzi
 Kód přizpůsobení na úrovni dokumentu obvykle sdílí hlavní vlákno uživatelského rozhraní aplikace Excel, takže všechny změny, které provedete v jazykové verzi vlákna, mají vliv na vše ostatní spuštěné v tomto vlákně. Změna není omezena na vaše přizpůsobení.

 Ovládací prvky model Windows Forms jsou inicializovány před spuštěním doplňku VSTO na úrovni aplikace spuštěné hostitelskou aplikací. V těchto situacích by měla být jazyková verze změněna před nastavením ovládacích prvků uživatelského rozhraní.

## <a name="install-the-language-packs"></a>Nainstalovat jazykové sady
 Pokud máte nastavení pro systém Windows, která nejsou anglická, můžete nainstalovat [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jazykové sady, abyste viděli [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zprávy ve stejném jazyce jako Windows. Pokud všichni koncoví uživatelé spouštějí vaše řešení s nastaveními, která nejsou v anglickém systému, musí mít správnou jazykovou sadu, aby viděli zprávy modulu runtime ve stejném jazyce jako Windows. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Jazykové sady jsou k dispozici na [webu služby Stažení softwaru](https://www.microsoft.com/download).

 Kromě toho jsou pro zprávy technologie ClickOnce nezbytné .NET Framework jazykové sady pro distribuci. .NET Framework jazykové sady jsou k dispozici na [webu Microsoft Download Center](https://www.microsoft.com/download).

## <a name="regional-settings-and-excel-com-calls"></a>Místní nastavení a volání v Excelu COM
 Pokaždé, když spravovaný klient zavolá metodu na objekt modelu COM a musí předat informace specifické pro jazykovou verzi, tak použije rozhraní <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (locale), které odpovídá aktuálnímu národnímu prostředí vlákna. Aktuální národní prostředí vlákna je ve výchozím nastavení děděno z místních nastavení uživatele. Nicméně při volání do modelu objektu aplikace Excel z řešení aplikace Excel, které bylo vytvořeno pomocí nástrojů pro vývoj pro Office v sadě Visual Studio, je formát dat English (USA) (locale ID 1033) předán do modelu objektu aplikace Excel automaticky. Je nutné formátovat všechna data, která mají formátování zohledňující národní prostředí, jako jsou data a měna, pomocí formátu dat anglické verze (USA), než je předáte systém Microsoft Office Excelu nebo si přečtěte data z kódu projektu.

## <a name="considerations-for-storing-data"></a>Předpoklady pro ukládání dat
 Chcete-li zajistit, aby vaše data byla správně interpretována a zobrazena, měli byste také zvážit, že problémy mohou nastat, pokud aplikace ukládá data, jako jsou například vzorce listu aplikace Excel, do řetězcových literálů (pevně zakódovaných) místo v objektech silného typu. Měli byste použít data, která jsou formátována za předpokladu, že jsou ve stylu invariantní nebo English (USA) jazykové verze (LCID Value 1033).

### <a name="applications-that-use-string-literals"></a>Aplikace, které používají řetězcové literály
 Možné hodnoty, které mohou být pevně zakódované, zahrnují literály data, které jsou zapsány ve formátu anglické verze (USA), a vzorce excelového listu, které obsahují lokalizované názvy funkcí. Další možností může být pevně zakódovaný řetězec, který obsahuje číslo, například "1 000"; v některých jazykových verzích je tato hodnota interpretována jako 1000, ale v jiných jazykových verzích představuje jeden bod nula. Výpočty a porovnání provedené v nesprávném formátu mohou mít za následek nesprávná data.

 Aplikace Excel interpretuje všechny řetězce v souladu s identifikátorem LCID, který je předán s řetězcem. To může být problém, pokud formát řetězce neodpovídá identifikátoru LCID, který je předán. Řešení aplikace Excel vytvořená pomocí vývojářských nástrojů Office v sadě Visual Studio při předávání všech dat používají LCID 1033 (EN-US). Aplikace Excel zobrazí data podle místních nastavení a jazyka uživatelského rozhraní aplikace Excel. Tento způsob funguje také v jazyk Visual Basic for Application (VBA); řetězce jsou formátovány jako en-US a VBA téměř vždy předává 0 (jazykově neutrální) jako LCID. Například následující kód VBA zobrazuje v souladu s aktuálním nastavením národního prostředí uživatele správnou naformátovanou hodnotu pro 12. května 2004:

```vb
'VBA
Application.ActiveCell.Value2 = "05/12/04"
```

 Stejný kód, při použití v řešení vytvořeném pomocí vývojářských nástrojů Office v sadě Visual Studio a předaných do aplikace Excel prostřednictvím zprostředkovatele komunikace s objekty COM, vytváří stejné výsledky, pokud je datum formátováno ve stylu en-US.

 Příklad:

 [!code-vb[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#6)]
 [!code-csharp[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#6)]

 Pokud je to možné, měli byste pracovat s daty silného typu namísto řetězcových literálů. Například místo uložení data v řetězcovém literálu ho uložte jako a <xref:System.Double> pak ho převeďte na <xref:System.DateTime> objekt pro manipulaci.

 Následující příklad kódu vyžaduje datum, kdy uživatel zadá do buňky A5, uloží ho jako a <xref:System.Double> pak ho převede na <xref:System.DateTime> objekt pro zobrazení v buňce A7. Aby bylo možné zobrazit datum, musí být buňka A7 naformátovaná.

 [!code-vb[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#7)]
 [!code-csharp[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#7)]

### <a name="excel-worksheet-functions"></a>Funkce listu aplikace Excel
 Názvy funkcí listu jsou interně přeložené pro většinu jazykových verzí Excelu. Vzhledem k tomu, že problémy s potenciálním voláním jazyka a modelu COM, je však doporučeno používat v kódu pouze anglické názvy funkcí.

### <a name="applications-that-use-external-data"></a>Aplikace, které používají externí data
 Jakýkoli kód, který se otevře nebo jinak používá externí data, například soubory, které obsahují hodnoty oddělené čárkami (soubory CSV) exportované ze starší verze systému, můžou být ovlivněné i v případě, že se takové soubory exportují pomocí libovolného formátu kromě en-US. Přístup k databázi nemusí být ovlivněn, protože všechny hodnoty by měly být v binárním formátu, pokud databáze neukládá data jako řetězce nebo provádí operace, které nepoužívají binární formát. Také Pokud vytváříte dotazy SQL pomocí dat z Excelu, možná budete muset zajistit, aby byly ve formátu en-US, v závislosti na funkci, kterou používáte.

## <a name="see-also"></a>Viz také

- [Postupy: cílení na vícejazyčné uživatelské rozhraní Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)