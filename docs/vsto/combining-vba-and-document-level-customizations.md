---
title: Kombinování přizpůsobení na úrovni VBA a dokumentů
description: Naučte se, jak můžete použít kód jazyk Visual Basic for Application (VBA) v dokumentu, který je součástí přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word nebo Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 59d0e9122bf35ac6f40799d91d3b52614d027f50
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846399"
---
# <a name="combine-vba-and-document-level-customizations"></a>Kombinování přizpůsobení na úrovni VBA a dokumentů
  Kód jazyk Visual Basic for Application (VBA) lze použít v dokumentu, který je součástí přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word nebo systém Microsoft Office Excel. Můžete volat kód VBA v dokumentu ze sestavení vlastního nastavení nebo můžete nakonfigurovat projekt tak, aby v dokumentu povoloval kód v sestavení pro volání kódu v sestavení přizpůsobení.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Chování kódu v jazyce VBA v přizpůsobení na úrovni dokumentu
 Když otevřete projekt v aplikaci Visual Studio, dokument se otevře v režimu návrhu. Kód VBA se nespustí, když je dokument v režimu návrhu, takže můžete pracovat na dokumentu a kódu bez spuštění kódu VBA.

 Když spustíte řešení, obslužné rutiny události v jazyce VBA a sestavení vlastního nastavení vyberou události, které jsou vyvolány v dokumentu, a obě sady kódu se spustí. Nemůžete předem určit, který kód se spustí před druhým; To je nutné zjistit v každém jednotlivém případě testováním. Pokud nejsou dvě sady kódů pečlivě koordinovány a testovány, můžete získat neočekávané výsledky.

## <a name="call-vba-code-from-the-customization-assembly"></a>Volání kódu jazyka VBA ze sestavení vlastního nastavení
 Makra můžete volat v dokumentech aplikace Word a v sešitech aplikace Excel můžete volat makra a funkce. K tomu použijte jednu z následujících metod:

- V případě aplikace Word volejte <xref:Microsoft.Office.Interop.Word._Application.Run%2A> metodu <xref:Microsoft.Office.Interop.Word.Application> třídy.

- V aplikaci Excel volejte <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> metodu <xref:Microsoft.Office.Interop.Excel.Application> třídy.

  Pro každou metodu určuje první parametr název makra nebo funkce, kterou chcete volat, a zbývající volitelné parametry určují parametry, které mají být předávány makru nebo funkci. První parametr může mít různé formáty pro Word a Excel:

- V případě aplikace Word je prvním parametrem řetězec, který může být libovolná kombinace šablony, modulu a názvu makra. Pokud zadáte název dokumentu, váš kód může spustit pouze makra v dokumentech souvisejících s aktuálním kontextem, nikoli pouze s žádným makrem v žádném dokumentu.

- V aplikaci Excel může být prvním parametrem řetězec, který určuje název makra, <xref:Microsoft.Office.Interop.Excel.Range> který označuje, kde je funkce, nebo ID registru pro funkci registrované knihovny DLL (XLL). Pokud předáte řetězec, vyhodnotí se řetězec v kontextu aktivního listu.

  Následující příklad kódu ukazuje, jak volat makro s názvem `MyMacro` z projektu na úrovni dokumentu pro aplikaci Excel. Tento příklad předpokládá, že `MyMacro` je definován v `Sheet1` .

```vb
Globals.Sheet1.Application.Run("MyMacro")
```

```csharp
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing);
```

> [!NOTE]
> Informace o použití globální `missing` proměnné místo volitelných parametrů v jazyce Visual C# naleznete v tématu [Write code in Office Solutions](../vsto/writing-code-in-office-solutions.md).

## <a name="call-code-in-document-level-customizations-from-vba"></a>Volání kódu v přizpůsobeních na úrovni dokumentu z jazyka VBA
 Můžete nakonfigurovat projekt na úrovni dokumentu pro aplikaci Word nebo Excel tak, aby kód jazyk Visual Basic for Application (VBA) v dokumentu mohl volat kód v sestavení přizpůsobení. To je užitečné v následujících scénářích:

- Chcete v dokumentu roztáhnout existující kód v jazyce VBA pomocí funkcí v přizpůsobení na úrovni dokumentu, které jsou přidruženy ke stejnému dokumentu.

- Chcete zpřístupnit služby, které vyvíjíte v přizpůsobení na úrovni dokumentu, k dispozici koncovým uživatelům, kteří mají přístup ke službám pomocí psaní kódu v jazyce VBA v dokumentu.

  Vývojové nástroje pro Office v sadě Visual Studio poskytují podobnou funkci pro doplňky VSTO. Při vývoji doplňku VSTO můžete volat kód v doplňku VSTO z jiných řešení systém Microsoft Office. Další informace najdete v tématu [kód volání v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

> [!NOTE]
> Tuto funkci nelze použít v projektech šablon aplikace Word. Dá se použít jenom v projektech aplikace Word, excelovém sešitu nebo excelových šablonách.

## <a name="requirements"></a>Požadavky
 Předtím, než můžete povolit kód VBA pro volání do sestavení vlastního nastavení, musí váš projekt splňovat následující požadavky:

- Dokument musí mít jednu z následujících přípon názvů souborů:

  - Pro Word: *. docm* nebo *. doc*

  - Pro Excel: *. xlsm*, *. xltm*, *. xls* nebo *. xlt*

- Dokument musí již obsahovat projekt VBA, který obsahuje kód VBA.

- Aby bylo možné spustit makra, musí být kód VBA v dokumentu spuštěn bez zobrazení výzvy uživateli. Můžete důvěřovat kódu VBA pro spuštění přidáním umístění projektu Office do seznamu důvěryhodných umístění v nastavení centra zabezpečení pro Word nebo Excel.

- Projekt sady Office musí obsahovat alespoň jednu veřejnou třídu, která obsahuje jednoho nebo více veřejných členů, které vystavujete do jazyka VBA.

     Můžete vystavit metody, vlastnosti a události v jazyce VBA. Vystavovaná třída může být třída hostitelské položky (například `ThisDocument` pro Word nebo `ThisWorkbook` i `Sheet1` pro Excel) nebo jiná třída, kterou definujete v projektu. Další informace o položkách hostitelů naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>Povolit kódu jazyka VBA volání do sestavení vlastního nastavení
 Existují dva způsoby, jak můžete zveřejnit členy v sestavení vlastního nastavení pro kód VBA v dokumentu:

- Můžete vystavit členy třídy položky hostitele v [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu do jazyka VBA. Chcete-li to provést, nastavte vlastnost **EnableVbaCallers** položky hostitel na **hodnotu true** v okně **vlastnosti** , zatímco položka hostitele (tj. dokument, list nebo sešit) je otevřena v návrháři. Visual Studio automaticky provádí veškerou práci nutnou k tomu, aby kód VBA mohl volat členy třídy.

- Můžete zveřejnit členy v libovolné veřejné třídě v projektu jazyka Visual C# nebo členy v třídě nehostitelské položky v [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu, do jazyka VBA. Tato možnost poskytuje větší volnost pro výběr tříd, které vystavíte pro jazyk VBA, ale také vyžaduje více ručních kroků.

   K tomu je třeba provést následující hlavní kroky:

  1. Vystavení třídy modelu COM.

  2. Přepište metodu **GetAutomationObject** třídy hostitelské položky v projektu tak, aby vracela instanci třídy, kterou vystavujete do jazyka VBA.

  3. Nastavte vlastnost **ReferenceAssemblyFromVbaProject** všech tříd hostitelských položek v projektu na **hodnotu true**. Tím se do sestavení vloží knihovna typů sestavení pro přizpůsobení a přidá odkaz na knihovnu typů do projektu VBA v dokumentu.

  Podrobné pokyny naleznete v tématu [How to: vystavení kódu v jazyce Visual Basic v projektu Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) a [Postupy: vystavení kódu pro jazyk VBA v projektu Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

  Vlastnosti **EnableVbaCallers** a **ReferenceAssemblyFromVbaProject** jsou k dispozici pouze v okně **vlastnosti** v době návrhu. nelze je použít v době běhu. Chcete-li zobrazit vlastnosti, otevřete návrháře pro položku hostitele v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Další informace o konkrétních úkolech, které Visual Studio provádí při nastavení těchto vlastností, najdete v tématu úlohy, které [provádí vlastnosti položky hostitele](#PropertyTasks).

> [!NOTE]
> Pokud sešit nebo dokument ještě neobsahuje kód VBA nebo pokud kód VBA v dokumentu není důvěryhodný ke spuštění, zobrazí se při nastavování vlastnosti **EnableVbaCallers** nebo **ReferenceAssemblyFromVbaProject** na **hodnotu true** chybová zpráva. Je to proto, že Visual Studio nemůže v této situaci upravovat projekt VBA v dokumentu.

## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>Použití členů v kódu VBA pro volání do sestavení vlastního nastavení
 Poté, co nakonfigurujete projekt tak, aby povoloval kód VBA pro volání do sestavení vlastního nastavení, Visual Studio přidá následující členy do projektu VBA v dokumentu:

- Pro všechny projekty Visual Studio přidá globální metodu s názvem `GetManagedClass` .

- Pro [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projekty, ve kterých zveřejňujete členy třídy položky hostitele pomocí vlastnosti **EnableVbaCallers** , Visual Studio také přidá vlastnost s názvem `CallVSTOAssembly` do `ThisDocument` `ThisWorkbook` modulu,,, `Sheet1` `Sheet2` nebo `Sheet3` v projektu VBA.

  `CallVSTOAssembly`Vlastnost nebo metodu lze použít `GetManagedClass` pro přístup k veřejným členům třídy, které jsou vystaveny pro kód VBA v projektu.

> [!NOTE]
> Během vývoje a nasazení řešení je k dispozici několik různých kopií dokumentu, kde můžete přidat kód VBA. Další informace najdete v tématu [pokyny pro přidání kódu v jazyce VBA do dokumentu](#Guidelines).

### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Použití vlastnosti CallVSTOAssembly v projektu Visual Basic
 Použijte `CallVSTOAssembly` vlastnost pro přístup k veřejným členům, které jste přidali do třídy položky hostitele. Například následující makro VBA volá metodu s názvem `MyVSTOMethod` , která je definována ve `Sheet1` třídě v projektu excelový sešit.

```vb
Sub MyMacro()
    Sheet1.CallVSTOAssembly.MyVSTOMethod()
End Sub
```

 Tato vlastnost je pohodlnější způsob, jak volat sestavení vlastního nastavení, než přímé použití `GetManagedClass` metody. `CallVSTOAssembly` Vrátí objekt, který představuje třídu hostitelské položky, kterou jste vystavili v jazyce VBA. V IntelliSense se zobrazí členy a parametry metody vráceného objektu.

 `CallVSTOAssembly`Vlastnost má deklaraci, která je podobná následujícímu kódu. Tento kód předpokládá, že jste vystavili `Sheet1` třídu hostitele v projektu excelového sešitu s názvem `ExcelWorkbook1` na VBA.

```vb
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1
    Set CallVSTOAssembly = GetManagedClass(Me)
End Property
```

### <a name="use-the-getmanagedclass-method"></a>Použití metody GetManagedClass
 Chcete-li použít globální `GetManagedClass` metodu, předejte objekt VBA, který odpovídá třídě položky hostitele, která obsahuje vaše přepsání metody **GetAutomationObject** . Pak použijte vrácený objekt pro přístup ke třídě, kterou jste vystavili v jazyce VBA.

 Například následující makro VBA volá metodu s názvem `MyVSTOMethod` , která je definována v `Sheet1` třídě položky hostitele v projektu excelového sešitu s názvem `ExcelWorkbook1` .

```vb
Sub CallVSTOMethod
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1
    Set VSTOSheet1 = GetManagedClass(Sheet1)
    VSTOSheet1.MyVSTOMethod
End Sub
```

 `GetManagedClass`Metoda má následující deklaraci.

```vb
GetManagedClass(pdispInteropObject Object) As Object
```

 Tato metoda vrátí objekt, který představuje třídu, kterou jste vystavili v jazyce VBA. V IntelliSense se zobrazí členy a parametry metody vráceného objektu.

## <a name="guidelines-for-adding-vba-code-to-the-document"></a><a name="Guidelines"></a> Pokyny pro přidání kódu v jazyce VBA do dokumentu
 Existuje několik různých kopií dokumentu, kde můžete přidat kód VBA, který volá do přizpůsobení na úrovni dokumentu.

 Při vývoji a testování řešení můžete napsat kód VBA v dokumentu, který se otevře během ladění nebo spuštění projektu v aplikaci Visual Studio (to znamená, že dokument ve výstupní složce sestavení). Veškerý kód VBA, který přidáte do tohoto dokumentu, však bude při příštím sestavení projektu přepsán, protože aplikace Visual Studio nahradí dokument ve výstupní složce sestavení kopií dokumentu z hlavní složky projektu.

 Pokud chcete uložit kód VBA, který přidáte do dokumentu během ladění nebo spuštění řešení, zkopírujte kód VBA do dokumentu ve složce projektu. Další informace o procesu sestavení naleznete v tématu [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

 Až budete připraveni k nasazení vašeho řešení, existují tři hlavní umístění dokumentů, ve kterých můžete přidat kód VBA.

### <a name="in-the-project-folder-on-the-development-computer"></a>Ve složce projektu ve vývojovém počítači
 Toto umístění je vhodné, pokud máte úplnou kontrolu nad kódem VBA v dokumentu i v kódu přizpůsobení. Vzhledem k tomu, že se dokument nachází ve vývojovém počítači, můžete kód VBA snadno upravit, pokud změníte kód přizpůsobení. Kód VBA, který přidáte do této kopie dokumentu, zůstane v dokumentu při sestavování, ladění a publikování řešení.

 Kód VBA nelze do dokumentu přidat, je-li otevřen v návrháři. Nejprve je nutné zavřít dokument v návrháři a pak dokument otevřít přímo v aplikaci Word nebo Excel.

> [!CAUTION]
> Pokud přidáte kód VBA, který se spustí při otevření dokumentu, ve výjimečných případech může tento kód poškodit dokument nebo zabránit otevření v návrháři.

### <a name="in-the-publish-or-installation-folder"></a>V adresáři pro publikování nebo instalaci
 V některých případech může být vhodné přidat kód VBA do dokumentu ve složce pro publikování nebo instalaci. Tuto možnost můžete zvolit například v případě, že kód VBA je napsán a testován jiným vývojářem v počítači, který nemá nainstalovánu aplikaci Visual Studio.

 Pokud uživatelé nainstalují řešení přímo ze složky publikování, je nutné přidat kód VBA do dokumentu při každém publikování řešení. Po publikování řešení přepíše aplikace Visual Studio dokument v umístění pro publikování.

 Pokud uživatelé nainstalují řešení z instalační složky, která se liší od složky pro publikování, můžete Nepřidávat kód VBA v dokumentu pokaždé, když řešení publikujete. Až bude aktualizace publikování připravena k přesunutí ze složky pro publikování do instalační složky, zkopírujte všechny soubory do instalační složky kromě dokumentu.

### <a name="on-the-end-user-computer"></a>Na počítači koncového uživatele
 Pokud jsou koncoví uživatelé vývojáři jazyka VBA, kteří volají služby, které zadáte v přizpůsobení na úrovni dokumentu, můžete jim sdělit, jak volat kód pomocí `CallVSTOAssembly` vlastnosti nebo `GetManagedClass` metody ve svých kopiích dokumentu. Když publikujete aktualizace řešení, kód VBA v dokumentu na počítači koncového uživatele nebude přepsán, protože aktualizace nejsou upraveny publikováním.

## <a name="tasks-performed-by-the-host-item-properties"></a><a name="PropertyTasks"></a> Úlohy prováděné vlastnostmi položky hostitele
 Když použijete vlastnosti **EnableVbaCallers** a **ReferenceAssemblyFromVbaProject** , Visual Studio provede různé sady úkolů.

### <a name="enablevbacallers"></a>EnableVbaCallers
 Při nastavení vlastnosti **EnableVbaCallers** položky hostitele na **hodnotu True** v projektu Visual Basic provede aplikace Visual Studio následující úlohy:

1. Přidá <xref:Microsoft.VisualBasic.ComClassAttribute> <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributy a do třídy položky hostitele.

2. Přepisuje metodu **GetAutomationObject** třídy položky hostitele.

3. Nastaví vlastnost **ReferenceAssemblyFromVbaProject** položky hostitele na **hodnotu true**.

   Pokud nastavíte vlastnost **EnableVbaCallers** zpět na **hodnotu false**, sada Visual Studio provede následující úlohy:

4. Odebere <xref:Microsoft.VisualBasic.ComClassAttribute> <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributy a z `ThisDocument` třídy.

5. Odebere metodu **GetAutomationObject** z třídy položky hostitele.

   > [!NOTE]
   > Sada Visual Studio automaticky nenastaví vlastnost **ReferenceAssemblyFromVbaProject** zpět na **hodnotu false (NEPRAVDA**). Tuto vlastnost lze nastavit na **hodnotu false** ručně pomocí okna **vlastnosti** .

### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject
 Je-li vlastnost **ReferenceAssemblyFromVbaProject** jakékoli položky hostitele v Visual Basic nebo v projektu jazyka Visual C# nastavena na **hodnotu true**, aplikace Visual Studio provede následující úlohy:

1. Vygeneruje knihovnu typů pro sestavení vlastního nastavení a vloží knihovnu typů do sestavení.

2. Do projektu VBA v dokumentu přidá odkaz na následující knihovny typů:

   - Knihovna typů pro sestavení vlastního nastavení.

   - Knihovna typů Microsoft Visual Studio nástrojů pro modul spouštění sady Office 9,0. Tato knihovna typů je obsažena v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

   Pokud je vlastnost **ReferenceAssemblyFromVbaProject** nastavena na **hodnotu false**, sada Visual Studio provede následující úlohy:

3. Odstraní odkazy knihovny typů z projektu VBA v dokumentu.

4. Odstraní vloženou knihovnu typů ze sestavení.

## <a name="troubleshoot"></a>Odstraňování potíží
 V následující tabulce jsou uvedeny některé běžné chyby a návrhy pro opravu chyb.

|Chyba|Návrh|
|-----------|----------------|
|Po nastavení vlastnosti **EnableVbaCallers** nebo **ReferenceAssemblyFromVbaProject** se zobrazí chybová zpráva oznamující, že dokument neobsahuje projekt VBA, nebo nemáte oprávnění pro přístup k projektu VBA v dokumentu.|Ujistěte se, že dokument v projektu obsahuje alespoň jedno makro VBA, projekt VBA má dostatečnou důvěryhodnost ke spuštění a projekt VBA není chráněn heslem.|
|Po nastavení vlastnosti **EnableVbaCallers** nebo **ReferenceAssemblyFromVbaProject** se zobrazí chybová zpráva oznamující, že <xref:System.Runtime.InteropServices.GuidAttribute> deklarace chybí nebo je poškozená.|Zajistěte, aby byla <xref:System.Runtime.InteropServices.GuidAttribute> deklarace v projektu v souboru *AssemblyInfo.cs* nebo *AssemblyInfo. vb* a zda je tento atribut nastaven na platný identifikátor GUID.|
|Když nastavíte vlastnost **EnableVbaCallers** nebo **ReferenceAssemblyFromVbaProject** , zobrazí se chybová zpráva, že číslo verze určené parametrem není <xref:System.Reflection.AssemblyVersionAttribute> platné.|Zajistěte, aby se <xref:System.Reflection.AssemblyVersionAttribute> deklarace v souboru *AssemblyInfo.cs* nebo *AssemblyInfo. vb* v projektu nastavila na platné číslo verze sestavení. Informace o platných číslech verzí sestavení naleznete v tématu <xref:System.Reflection.AssemblyVersionAttribute> Třída.|
|Po přejmenování sestavení přizpůsobení přestane fungovat kód VBA, který volá do sestavení vlastního nastavení.|Pokud změníte název sestavení přizpůsobení po jeho zveřejnění kódu v jazyce VBA, propojení mezi projektem VBA v dokumentu a sestavením vlastního nastavení je přerušeno. Chcete-li tento problém vyřešit, změňte vlastnost **ReferenceFromVbaAssembly** v projektu na **hodnotu false** a potom zpět na **hodnotu true** a potom nahraďte všechny odkazy na starý název sestavení v kódu VBA novým názvem sestavení.|

## <a name="see-also"></a>Viz také
- [Postupy: vystavení kódu v projektu Visual Basic v jazyce VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Postupy: vystavení kódu pro jazyk VBA ve Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Návod: volání kódu z jazyka VBA v projektu Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Návod: volání kódu z jazyka VBA ve Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Srovnání řešení VBA a Office v sadě Visual Studio](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
