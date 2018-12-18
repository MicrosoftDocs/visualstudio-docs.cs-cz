---
title: Kombinování přizpůsobení na úrovni dokumentu a VBA
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2243a3e03ed84325523f62d77ae3cc6d20f83bbb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878073"
---
# <a name="combine-vba-and-document-level-customizations"></a>Kombinování přizpůsobení na úrovni dokumentu a VBA
  Používat Visual Basic for Applications (VBA) kódu v dokumentu, který je součástí přizpůsobení úrovni dokumentu pro aplikaci Microsoft Office Word nebo Microsoft Office Excel. Můžete volat kód VBA v dokumentu z vlastního nastavení sestavení nebo projektu, aby umožňoval kód VBA v dokumentu k volání kódu v sestavení přizpůsobení můžete nakonfigurovat.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Chování kód VBA v přizpůsobení na úrovni dokumentu  
 Když otevřete projekt v sadě Visual Studio, dokument je otevřen v režimu návrhu. Dokument je v režimu návrhu, abyste mohli pracovat bez spuštění kódu jazyka VBA v dokumentu a kód VBA kód nespustí.  
  
 Při spuštění řešení obslužné rutiny událostí v VBA a vlastního nastavení sestavení odráželo události, které jsou vyvolány v dokumentu a spustit obě sady kódu. Nelze předem určit, jaký kód se spustí před dalšími; To je třeba určit pomocí testování ve všech jednotlivých případech. Pokud není pečlivě koordinovaný a testování dvě sady kódu můžete získat neočekávané výsledky.  
  
## <a name="call-vba-code-from-the-customization-assembly"></a>Volání kódu z vlastního nastavení sestavení  
 Makra může volat do dokumentů aplikace Word a volání makra a funkce v sešitech aplikace Excel. K tomuto účelu použijte jednu z následujících metod:  
  
- Pro Word, zavolejte <xref:Microsoft.Office.Interop.Word._Application.Run%2A>metodu <xref:Microsoft.Office.Interop.Word.Application> třídy.  
  
- Pro aplikaci Excel, zavolejte <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> metodu <xref:Microsoft.Office.Interop.Excel.Application> třídy.  
  
  Pro každou metodu první parametr určuje název makra nebo funkci, kterou chcete volat a zbývající nepovinné parametry zadejte parametry k předání do funkce i makra. První parametr může mít různé formáty pro aplikace Word a Excel:  
  
- Pro Word první parametr je řetězec, který může být libovolná kombinace šablony, modul a název makra. Pokud zadáte název dokumentu, váš kód lze spustit pouze makra v dokumentech související s aktuálním kontextu, není to jen tak nějaký – makro v libovolném dokumentu.  
  
- Pro aplikaci Excel, může být první parametr řetězec určující název makra <xref:Microsoft.Office.Interop.Excel.Range> , která indikuje, ve kterém je daná funkce nebo ID registrace pro registrované funkci knihovny DLL (XLL). Pokud předáte řetězec, řetězec se vyhodnotí v kontextu aktivní list.  
  
  Následující příklad kódu ukazuje, jak volat makro s názvem `MyMacro` z projektu úrovni dokumentu pro Excel. Tento příklad předpokládá, že `MyMacro` je definována v `Sheet1`.  
  
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
>  Další informace o použití globálního `missing` proměnnou místo volitelné parametry v jazyce Visual C# naleznete v tématu [psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="call-code-in-document-level-customizations-from-vba"></a>Volání kódu v přizpůsobeních na úrovni dokumentu z jazyka VBA  
 Můžete nakonfigurovat úrovni dokumentu projektu pro aplikaci Word nebo Excel, tento kód Visual Basic for Applications (VBA) v dokumentu může volat kód v sestavení přizpůsobení. To je užitečné v následujících scénářích:  
  
- Chcete rozšířit existující kód VBA v dokumentu s využitím funkcí v přizpůsobení úrovni dokumentu, který je spojen s stejný dokument.  
  
- Chcete zpřístupnit služby, které vyvíjíte v přizpůsobení na úrovni dokumentu koncovým uživatelům, kteří můžou přístup ke službám napsáním kódu jazyka VBA v dokumentu.  
  
  Vývojářské nástroje balíku Office v sadě Visual Studio poskytuje podobné funkce pro doplňky VSTO. Pokud vyvíjíte doplňku VSTO, můžete volat kódu v doplňku VSTO z jiných řešení pro Microsoft Office. Další informace najdete v tématu [volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
> [!NOTE]  
>  Tuto funkci nelze použít v projektech aplikace Word šablony. Je možné pouze v Wordový dokument, sešit aplikace Excel nebo projektů šablona aplikace Excel.  
  
## <a name="requirements"></a>Požadavky  
 Před povolením kód VBA, chcete-li volat vlastního nastavení sestavení, váš projekt musí splňovat následující požadavky:  
  
-   Dokument musí mít jednu z následujících přípony názvů souborů:  
  
    -   Pro Word: *DOCM* nebo *doc*  
  
    -   Pro aplikaci Excel: *.xlsm*, *.xltm*, *.xls*, nebo *.xlt*  
  
-   Dokument již musí obsahovat projekt VBA, který má kód VBA v ní.  
  
-   Kód VBA v dokumentu musíte bude moct spouštět bez výzvy pro uživatele povolit makra. VBA kód ke spuštění tak, že přidáte do seznamu důvěryhodných umístění v nastavení Centra zabezpečení pro aplikaci Word nebo Excel umístění projektu Office, kterému můžete důvěřovat.  
  
-   Projekt sady Office musí obsahovat alespoň jednu veřejnou třídu, která obsahuje jeden nebo více veřejné členy, které jsou vystaveny pro jazyk VBA.  
  
     Můžete zpřístupnit metody, vlastnosti a události pro jazyk VBA. Třída, která zveřejníte může být třída položky hostitele (například `ThisDocument` pro Word, nebo `ThisWorkbook` a `Sheet1` pro Excel) nebo jiné třídy, které definujete ve vašem projektu. Další informace o hostitelských položkách naleznete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>Povolit kód VBA, chcete-li volat vlastního nastavení sestavení  
 Existují dva různé způsoby, můžete zveřejnit členy v vlastního nastavení sestavení pro kód VBA v dokumentu:  
  
- Můžete zveřejnit členy třídy položku hostitele v [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projekt VBA. Chcete-li to provést, nastavte **EnableVbaCallers** vlastnost položky hostitele **True** v **vlastnosti** je okno při hostitelská položka (to znamená, dokument, listu nebo sešitu) v Návrháři otevřený. Visual Studio automaticky provede všechny práci potřebnou k povolení VBA kód volat členy třídy.  
  
- Můžete zveřejnit členy libovolné veřejné třídy v projektu jazyka Visual C# nebo třída v členy v jiné než hostitelské položky [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu pro jazyk VBA. Tato možnost vám poskytne větší možnosti zvolte třídy, které zpřístupníte VBA, ale také vyžaduje další ruční kroky.  
  
   Chcete-li to provést, je třeba provést následující hlavní kroky:  
  
  1.  Vystavení třídy do modelu COM.  
  
  2.  Přepsat **GetAutomationObject** metoda třídy položku hostitele ve vašem projektu a vrátit instanci třídy, které jsou vystaveny pro jazyk VBA.  
  
  3.  Nastavte **ReferenceAssemblyFromVbaProject** vlastnost všechny hostitele položku třídy v projektu a **True**. To vloží vlastní nastavení sestavení knihovny typů do sestavení a přidá odkaz na knihovnu typů do projektu VBA v dokumentu.  
  
  Podrobné pokyny najdete v tématu [postupy: vystavení kódu do VBA v projektu jazyka Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) a [postupy: vystavení kódu v aplikaci Visual C pro jazyk VBA&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
  **EnableVbaCallers** a **ReferenceAssemblyFromVbaProject** jsou k dispozici pouze ve vlastnosti **vlastnosti** okno v době návrhu, nelze je použít v době běhu . Chcete-li zobrazit vlastnosti, otevřete návrhář pro položku hostitele v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Další informace o konkrétních úloh, které Visual Studio provádí při nastavování těchto vlastností najdete v tématu [úlohy prováděné vlastnosti hostitele](#PropertyTasks).  
  
> [!NOTE]  
>  Pokud sešit nebo dokument už neobsahuje kód VBA, nebo pokud kód VBA v dokumentu není důvěryhodný pro spuštění, zobrazí se chybová zpráva při nastavení **EnableVbaCallers** nebo **ReferenceAssemblyFromVbaProject**  vlastnost **True**. Je to proto, že Visual Studio nelze upravit projektu VBA v dokumentu v této situaci.  
  
## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>Použití členů v kód VBA pro volání do vlastního nastavení sestavení  
 Po dokončení konfigurace projektu, aby umožňoval kód VBA, chcete-li volat vlastního nastavení sestavení Visual Studio přidá následující členy do projektu VBA v dokumentu:  
  
- Pro všechny projekty aplikace Visual Studio přidá globální metodu s názvem `GetManagedClass`.  
  
- Pro [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektů, ve kterých je zveřejnit členy hostitele třída položky pomocí **EnableVbaCallers** vlastnost, Visual Studio také přidává vlastnost s názvem `CallVSTOAssembly` k `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, nebo `Sheet3` modulu v projektu VBA.  
  
  Můžete použít `CallVSTOAssembly` vlastnost nebo `GetManagedClass` metody pro přístup k veřejné členy třídy, která je vystavená pro kód VBA v projektu.  
  
> [!NOTE]  
>  Při vývoji a nasazení vašeho řešení, existují různé kopie dokumentu ve kterém můžete přidat kód VBA. Další informace najdete v tématu [kódu pokyny pro přidání VBA v dokumentu](#Guidelines).  
  
### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Vlastnost CallVSTOAssembly použít v projektu jazyka Visual Basic  
 Použití `CallVSTOAssembly` vlastnosti pro přístup k veřejné členy, které jste přidali do třídy položku hostitele. Například následující makra VBA volá metodu s názvem `MyVSTOMethod` , která je definována v `Sheet1` třídu v projektu sešitu aplikace Excel.  
  
```vb
Sub MyMacro()  
    Sheet1.CallVSTOAssembly.MyVSTOMethod()  
End Sub  
```  
  
 Tato vlastnost je pohodlnější způsob, jak provádět volání do vlastního nastavení sestavení než při použití `GetManagedClass` metoda přímo. `CallVSTOAssembly` Vrátí objekt, který reprezentuje hostitele. Třída položek, která je vystavena pro jazyk VBA. V technologii IntelliSense zobrazí členy a parametry metody vráceného objektu.  
  
 `CallVSTOAssembly` Vlastnost má deklarace, která se podobá následující kód. Tento kód předpokládá, že mají přístup `Sheet1` hostovat položku třídy v projektu sešitu aplikace Excel s názvem `ExcelWorkbook1` pro jazyk VBA.  
  
```vb 
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1  
    Set CallVSTOAssembly = GetManagedClass(Me)  
End Property  
```  
  
### <a name="use-the-getmanagedclass-method"></a>Pomocí této metody GetManagedClass  
 Použít globální `GetManagedClass` metoda, předejte objekt VBA, který odpovídá na třídu položky hostitele, který obsahuje přepsání metody **GetAutomationObject** metody. Potom použijte vráceného objektu pro přístup ke třídě, která je vystavena VBA.  
  
 Například následující makra VBA volá metodu s názvem `MyVSTOMethod` , která je definována v `Sheet1` hostovat položku třídy v projektu sešitu aplikace Excel s názvem `ExcelWorkbook1`.  
  
```vb
Sub CallVSTOMethod  
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1  
    Set VSTOSheet1 = GetManagedClass(Sheet1)  
    VSTOSheet1.MyVSTOMethod  
End Sub  
```  
  
 `GetManagedClass` Metoda má následující deklarace.  
  
```vb
GetManagedClass(pdispInteropObject Object) As Object  
```  
  
 Tato metoda vrátí objekt, který představuje třídu, která je vystavena pro jazyk VBA. V technologii IntelliSense zobrazí členy a parametry metody vráceného objektu.  
  
##  <a name="Guidelines"></a> Pokyny pro přidání kód VBA v dokumentu  
 Existují různé kopie dokumentu ve kterém můžete přidat kód VBA, který volá do přizpůsobení úrovni dokumentu.  
  
 Jak vyvíjet a testovat vaše řešení, můžete napsat kód VBA v dokumentu, který se otevře při ladění nebo spuštění projektu v sadě Visual Studio (to znamená, že dokument ve výstupní složce sestavení). Ale libovolný kód VBA, který jste do tohoto dokumentu přidejte budou přepsány při příštím sestavení projektu, protože Visual Studio nahradí kopii dokumentu ze složky projektu hlavní dokument ve výstupní složce sestavení.  
  
 Pokud chcete uložit kód VBA, který přidáte do dokumentu během ladění nebo spuštění řešení, zkopírujte kód VBA do dokumentu ve složce projektu. Další informace o procesu sestavení naleznete v tématu [vytvářet řešení pro systém office](../vsto/building-office-solutions.md).  
  
 Jakmile budete připraveni k nasazení svého řešení, existují tři hlavní dokument umístění, ve kterých můžete přidat kód VBA.  
  
### <a name="in-the-project-folder-on-the-development-computer"></a>Ve složce projektu ve vývojovém počítači  
 Toto umístění je vhodné, pokud máte plnou kontrolu nad kód VBA v dokumentu a vlastním kódu. Protože dokument je na vývojovém počítači, můžete snadno upravit kód VBA, pokud změníte vlastním kódu. Kód VBA, který přidáte do této kopii dokumentu zůstane v dokumentu, při vytváření, ladění a publikování vašeho řešení.  
  
 Zatímco je otevřen v návrháři, nelze přidat kód VBA v dokumentu. Musíte nejprve zavřít dokument v návrháři a potom otevřete dokument přímo v aplikaci Word nebo Excel.  
  
> [!CAUTION]  
>  Pokud chcete přidat kód VBA, který se spustí při otevření dokumentu, ve výjimečných případech tento kód může poškodit dokumentu nebo brání jeho otevření v návrháři.  
  
### <a name="in-the-publish-or-installation-folder"></a>Ve složce instalace nebo publikovat  
 V některých případech může být vhodné přidat kód VBA v dokumentu ve složce instalace nebo publikovat. Například můžete zvolit tuto možnost, pokud kód VBA, je vytvoření a otestování různých vývojáři, kteří v počítači, který nemá nainstalovanou sadu Visual Studio.  
  
 Pokud si uživatelé nainstalují přímo ze složky publikovat řešení, je nutné přidat kód VBA v dokumentu, při každém publikování řešení. Visual Studio přepíše dokumentu v umístění pro publikování, při publikování řešení.  
  
 Pokud uživatelé řešení instalují z instalační složky, která se liší od složky publikování, můžete se vyhnout přidávání kód VBA v dokumentu, při každém publikování řešení. Při publikování aktualizace je připraven k přesunutí z složky publikování do instalační složky, zkopírujte všechny soubory do složky instalace s výjimkou dokumentu.  
  
### <a name="on-the-end-user-computer"></a>V počítači koncového uživatele  
 Pokud koncoví uživatelé budou VBA vývojáři, kteří jsou volání do služeb, které zadáte v přizpůsobení na úrovni dokumentu, můžete jim říct volání kódu s použitím `CallVSTOAssembly` vlastnost nebo `GetManagedClass` metoda v jejich kopií dokumentu. Při publikování aktualizací do řešení kód VBA v dokumentu v počítači koncového uživatele nedojde k přepsání, protože dokument není upraven metodou publikovat aktualizace.  
  
##  <a name="PropertyTasks"></a> Úlohy prováděné ve vlastnostech položky hostitele  
 Při použití **EnableVbaCallers** a **ReferenceAssemblyFromVbaProject** vlastnosti, Visual Studio provede různé sady úloh.  
  
### <a name="enablevbacallers"></a>EnableVbaCallers  
 Při nastavení **EnableVbaCallers** vlastnosti položky hostitele do **True** v projektu jazyka Visual Basic, Visual Studio provede následující úlohy:  
  
1. Přidá <xref:Microsoft.VisualBasic.ComClassAttribute> a <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributy do třídy položku hostitele.  
  
2. Přepíše **GetAutomationObject** metoda třídy položku hostitele.  
  
3. Nastaví **ReferenceAssemblyFromVbaProject** vlastnost položky hostitele **True**.  
  
   Při nastavení **EnableVbaCallers** vlastnost zpět do **False**, Visual Studio provede následující úlohy:  
  
4. Odebírá <xref:Microsoft.VisualBasic.ComClassAttribute> a <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributy z `ThisDocument` třídy.  
  
5. Odebírá **GetAutomationObject** metodu z třídy položku hostitele.  
  
   > [!NOTE]  
   >  Visual Studio automaticky nenastaví **ReferenceAssemblyFromVbaProject** vlastnost zpět do **False**. Tuto vlastnost lze nastavit **False** ručně pomocí **vlastnosti** okna.  
  
### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject  
 Když **ReferenceAssemblyFromVbaProject** libovolné položky hostitele v projektu jazyka Visual Basic nebo Visual C# je nastavena na **True**, Visual Studio provede následující úlohy:  
  
1. Vytvoří knihovnu typů pro vlastní nastavení sestavení a vloží knihovnu typů do sestavení.  
  
2. To přidá odkaz na následující knihovny typů v projektu VBA v dokumentu:  
  
   -   Knihovny typů pro vaše vlastní nastavení sestavení.  
  
   -   Microsoft Visual Studio Tools for Office spuštění modulu 9.0 knihovny typů. Je součástí této knihovny typů [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
   Když **ReferenceAssemblyFromVbaProject** je nastavena zpět na **False**, Visual Studio provede následující úlohy:  
  
3. Odkazy typu knihovny se odebere z projektu VBA v dokumentu.  
  
4. Vložený typ knihovny se odebere ze sestavení.  
  
## <a name="troubleshoot"></a>Řešení potíží
 Následující tabulka uvádí některé běžné chyby a návrhy pro opravu chyb.  
  
|Chyba|Návrh|  
|-----------|----------------|  
|Jakmile nastavíte **EnableVbaCallers** nebo **ReferenceAssemblyFromVbaProject** vlastnost, chybová zpráva uvádí, že dokument neobsahuje projekt VBA, nebo nemáte oprávnění k přístupu Projekt VBA v dokumentu.|Zajistěte, aby dokument v projektu obsahuje alespoň jedno makro VBA, má dostatečná vztahu důvěryhodnosti pro spuštění projektu VBA a projekt VBA není chráněn heslem.|  
|Jakmile nastavíte **EnableVbaCallers** nebo **ReferenceAssemblyFromVbaProject** vlastnost, chybová zpráva uvádí, že <xref:System.Runtime.InteropServices.GuidAttribute> deklarace je chybějící nebo poškozené.|Ujistěte se, že <xref:System.Runtime.InteropServices.GuidAttribute> deklarace se nachází v *AssemblyInfo.cs* nebo *AssemblyInfo.vb* soubor v projektu, a že tento atribut je nastaven na platný identifikátor GUID.|  
|Po nastavení **EnableVbaCallers** nebo **ReferenceAssemblyFromVbaProject** vlastnost, chybová zpráva uvádí, že číslo verze určená <xref:System.Reflection.AssemblyVersionAttribute> není platný.|Ujistěte se, že <xref:System.Reflection.AssemblyVersionAttribute> deklarace *AssemblyInfo.cs* nebo *AssemblyInfo.vb* soubor v projektu je nastavený na číslo verze platné sestavení. Informace o číslech verzí platné sestavení naleznete v tématu <xref:System.Reflection.AssemblyVersionAttribute> třídy.|  
|Po přejmenování vlastního nastavení sestavení kód VBA, který volá do vlastního nastavení sestavení přestane fungovat.|Pokud změníte název vlastního nastavení sestavení po vystavení pro kód VBA, dojde k přerušení propojení mezi projektu VBA v dokumentu a vlastního nastavení sestavení. Chcete-li tento problém vyřešit, změňte **ReferenceFromVbaAssembly** vlastnosti ve vašem projektu a **False** a pak zpátky **True**a potom nahraďte všechny odkazy na staré sestavení název v kód VBA s novým názvem sestavení.|  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: vystavení kódu do VBA v projektu jazyka Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Postupy: vystavení kódu v aplikaci Visual C pro jazyk VBA&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Návod: Volání kódu z jazyka VBA v projektu jazyka Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Návod: Volání kódu z jazyka VBA v aplikaci Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)   
 [Řešení VBA a Office v sadě Visual Studio porovnání](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)   
 [Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md)  
  
  