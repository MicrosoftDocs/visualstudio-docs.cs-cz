---
title: Specifické aspekty zabezpečení pro řešení pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dcb2e0a3c381b1dd07c7724c3a64c53307856014
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951389"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Specifické aspekty zabezpečení pro řešení pro systém Office
  Funkce zabezpečení poskytované rozhraní Microsoft .NET Framework a Microsoft Office může pomoct chránit vaše řešení pro systém Office proti možné bezpečnostní hrozby. Toto téma vysvětluje některé z těchto hrozeb a poskytuje doporučení, která pomáhá chránit před nimi. Obsahuje také informace o vlivu řešení pro systém Office v nastavení zabezpečení systému Microsoft Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Důvěryhodný kód je k jinému účelu v nových škodlivých dokumentu  
 Útočník může trvat důvěryhodný kód, který je určený pro jeden konkrétní účel, například stahování osobní informace pro pracovní aplikace, a znovu ji použít v jiném dokumentu, jako je například list. Kód není známo, že neběží původního dokumentu a dalšími hrozbami, jako je například odhalují osobní údaje nebo provádění kódu pomocí zvýšení oprávnění, když je otevře jiný uživatel může otevřít. Útočník Alternativně lze upravovat data v listu, tak, že při odeslání oběti, se chová neočekávaně. Změnou hodnoty, vzorce nebo prezentace charakteristiky listu propojené s kódem, je možné, uživatel se zlými úmysly k útoku na jiného uživatele zasláním upravený soubor. Může být také uživatelům přístup k informacím, které by neměl zobrazíte tak, že upravíte hodnoty v listu.  
  
 Protože umístění sestavení a umístění dokumentu musí mít dostatečná doklad provést, není tento útok snadno připojit. Například dokumenty v příloh e-mailu nebo v nedůvěryhodné intranetové servery nemají dostatečná oprávnění ke spuštění.  
  
 Chcete-li tento útok je to možné, samotný kód musí být napsané tak, že díky rozhodnutí založené na potenciálně nedůvěryhodná data. Příkladem je vytvoření list, který má skryté buňku, která obsahuje název databázového serveru. Uživatel odešle do listu do stránky ASPX, která se pokusí připojit k tomuto serveru pomocí ověřování SQL a pevně zakódované heslo SA. Útočník by mohl nahraďte obsah buňky skryté jiného názvu počítače a získejte heslo SA. Vyhněte se tento problém, nikdy pevně zakódovat hesla a vždy zkontrolujte ID serveru na interní seznam serverů, které jsou známé jako dobré před přístupem k serveru.  
  
### <a name="recommendations"></a>Doporučení  
  
-   Vždy ověřte vstup a data, ať už pochází od uživatele, dokument, databáze, webová služba nebo kterýkoli jiný zdroj.  
  
-   Buďte opatrní vystavení konkrétní typy funkcí, jako je například privileged data jménem uživatele a jejich zařazení do nechráněné listu.  
  
-   V závislosti na typu aplikace může mít smysl ověřte, zda je spuštěna v původním dokumentu před spuštěním jakéhokoli kódu. Ověřte například, že je spuštěná z dokumentu uloženou v známých a zabezpečené umístění.  
  
-   Může být vhodné zobrazit upozornění, když dokument se otevře, pokud aplikace provádí všechny privilegované akce. Například může vytvořit úvodní obrazovky nebo spuštění dialogové okno oznamující, že aplikace bude přístup k osobním informacím a mít uživatele, vyberte pokračovat nebo zrušit. Pokud koncový uživatel získá takové upozornění z zdánlivě nevinnosti dokumentu, budou moct ukončit aplikaci předtím, než dojde k ohrožení cokoli.  
  
## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Kód je blokována ochrana modelů objektů aplikace Outlook  
 Microsoft Office můžete zabránit pomocí určité vlastnosti, metody a objekty v objektovém modelu kódu. Omezením přístupu k těmto objektům Outlook pomáhá zabránit jsou červi, kteří e-mailu a viry pomocí objektového modelu ke škodlivým účelům. Tuto funkci zabezpečení se označuje jako ochrana modelů objektů aplikace Outlook. Pokud doplňku VSTO pokusí použít s omezeným přístupem vlastnosti nebo metody, když je povolená ochrana modelů objektů, zobrazí se upozornění zabezpečení, který umožňuje uživateli zastavení operace nebo umožňuje uživateli udělit přístup k vlastnosti nebo metody po omezenou dobu t Editor IME. Pokud uživatel zastaví prováděnou operaci, vyvolá výjimku Outlook doplňků VSTO vytvořené pomocí řešení pro systém Office v sadě Visual Studio <xref:System.Runtime.InteropServices.COMException>.  
  
 Ochrana modelů objektu může ovlivnit doplňků VSTO různými způsoby v závislosti na tom, zda se používá aplikace Outlook s Microsoft Exchange Server:  
  
- Pokud aplikace Outlook se nepoužívá se serverem Exchange, správce můžete povolit nebo zakázat ochrana modelů objektů pro všechny doplňků VSTO na počítači.  
  
- Outlook se používá s Exchangem, může správce povolit nebo zakázat ochrana modelů objektů pro všechny doplňků VSTO na počítači nebo může správce určit, aniž se objeví ochrana modelů objektu lze spustit některé Add-ins VSTO. Správci mohou také upravit chování ochrana modelů objektů v určitých oblastech objektového modelu. Například Správci mohou automaticky povolit doplňků VSTO pro odeslání e-mailu prostřednictvím kódu programu, i když je povolená ochrana modelů objektu.  
  
  Spouští se v aplikaci Outlook 2007, chování ochrana modelů objektu se změnil na zlepšení zkušeností vývojářů a uživatelů současně pomáhá zabezpečit aplikace Outlook. Další informace najdete v tématu [kódu změny zabezpečení v aplikaci Outlook 2007](http://go.microsoft.com/fwlink/?LinkId=73429).  
  
### <a name="minimize-object-model-guard-warnings"></a>Minimalizovat objektu modelu guard upozornění  
 Pokud chcete vyhnout upozornění zabezpečení při použití s omezeným přístupem vlastnostem a metodám, ujistěte se, že váš doplněk VSTO získá objektů aplikace Outlook z `Application` pole `ThisAddIn` třídu ve vašem projektu. Další informace o tomto poli, naleznete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Ochrana modelů objektu můžete důvěřovat pouze objektů aplikace Outlook získán z tohoto objektu. Naproti tomu objekty, které jsou získávány z nové `Microsoft.Office.Interop.Outlook.Application` objektu nejsou důvěryhodné, a s omezeným přístupem vlastnosti a metody se vyvolat upozornění zabezpečení, pokud je povolená ochrana modelů objektu.  
  
 Následující příklad kódu zobrazuje bezpečnostní upozornění, pokud je povolená ochrana modelů objektu. `To` Vlastnost `Microsoft.Office.Interop.Outlook.MailItem` třídy je omezený ochrana modelů objektu. `Microsoft.Office.Interop.Outlook.MailItem` Objektu není důvěryhodný, protože kód získá z `Microsoft.Office.Interop.Outlook.Application` , který je vytvořený pomocí **nové** operátor místo získávání z `Application` pole.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]  
  
 Následující příklad kódu ukazuje, jak používat s omezeným přístupem k vlastnosti `Microsoft.Office.Interop.Outlook.MailItem` objekt, který je důvěryhodný pro ochrana modelů objektu. Tento kód použije důvěryhodného `Application` pole zobrazíte `Microsoft.Office.Interop.Outlook.MailItem`.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]  
  
> [!NOTE]  
>  Pokud použijete Outlook s Exchangem, získání všech objektů aplikace Outlook z `ThisAddIn.Application` nezaručuje, že váš doplněk VSTO bude mít přístup k celé objektový model aplikace Outlook. Například pokud správce Exchange Outlook automaticky nastaví na Odepřít všechny pokusy o přístup k informacím adresu použití objektového modelu aplikace Outlook, aplikaci Outlook nebude předchozí příklad kódu pro přístup k vlastnosti na povolit i v případě, že příklad kódu používá důvěryhodné `ThisAddIn.Application` pole.  
  
### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Zadejte které Add-ins důvěřovat při používání systému Exchange  
 Při použití aplikace Outlook s Exchangem správci mohou určit spuštění některých Add-ins VSTO aniž se objeví ochrana modelů objektu. Aplikace Outlook doplňků VSTO vytvořené pomocí řešení pro systém Office v sadě Visual Studio nemůže být důvěryhodný samostatně. může být pouze důvěryhodné jako skupinu.  
  
 Aplikace Outlook důvěřuje doplňku VSTO na základě kódu hodnoty hash z vstupního bodu DLL doplňku VSTO. Všechny aplikace Outlook doplňků VSTO, které se zaměřují [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] použít stejnou knihovnu DLL vstupního bodu (*knihovna VSTOLoader.dll*). To znamená, že pokud správce důvěřuje jakékoli doplňku VSTO, který se zaměřuje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ke spuštění aniž se objeví ochrana modelů objektu a pak všechny ostatní VSTO doplňky, které se zaměřují [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jsou také důvěryhodné. Další informace o nastavení důvěryhodnosti konkrétní doplňků VSTO pro spuštění aniž se objeví ochrana modelů objektů najdete v tématu [zadejte metodu, aplikace Outlook se používá ke správě funkcí antivirové ochrany před únikem informací](http://go.microsoft.com/fwlink/?LinkId=128773).  
  
## <a name="permission-changes-do-not-take-effect-immediately"></a>Změny oprávnění provedené neprojevila okamžitě  
 Pokud správce upraví oprávnění pro dokument nebo sestavení, musí uživatelé ukončete a restartujte všechny aplikace Office pro tyto změny, která budou vynucena.  
  
 Jiné aplikace, které hostují aplikace Microsoft Office může také bránit zabraňuje nová oprávnění. Uživatelé by měl ukončete všechny aplikace, které používají Office, hostovaných i samostatné, když se změní zásady zabezpečení.  
  
## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Nastavení Centra zabezpečení v systému Microsoft Office nemají vliv na doplňky nebo přizpůsobení na úrovni dokumentu  
 Uživatele můžete zabránit doplňků VSTO načítání nastavením možnost v **centrum**. Však nejsou vytvořené pomocí řešení pro systém Office v sadě Visual Studio přizpůsobení úrovni dokumentu a doplňky VSTO vliv těchto nastavení vztahu důvěryhodnosti.  
  
 Pokud uživatel s použitím doplňků VSTO brání v načítání **centrum**, následující typy doplňků VSTO nenačte:  
  
- Spravovaného a nespravovaného COM doplňků VSTO.  
  
- Spravované a nespravované Chytré dokumenty.  
  
- Spravované a nespravované automatizaci VSTO doplňky.  
  
- Komponenty spravovaných a nespravovaných dat v reálném čase.  
  
  Následující postupy popisují, jak můžou uživatelé používat **centrum** omezit doplňků VSTO načítání v aplikaci Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a Microsoft Office 2010. Tyto postupy nemají vliv na doplňky VSTO nebo přizpůsobení vytvořené pomocí nástroje pro vývoj pro Office v sadě Visual Studio.  
  
#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice15shortvstoincludesoffice-15-short-mdmd-applications"></a>Chcete-li zakázat doplňků VSTO v Microsoft Office 2010 a Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] aplikací  
  
1.  Zvolte **souboru** kartu.  
  
2.  Zvolte *ApplicationName* **možnosti** tlačítko.  
  
3.  V podokně Kategorie vyberte **centrum**.  
  
4.  V podokně podrobností vyberte **nastavení Centra zabezpečení**.  
  
5.  V podokně Kategorie vyberte **Add-ins**.  
  
6.  V podokně podrobností vyberte **doplňky vyžadují aplikace podepsané důvěryhodným vydavatelem** nebo **zakázat všechny doplňky aplikací**.  
  
## <a name="see-also"></a>Viz také:  
 [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)  
  
  