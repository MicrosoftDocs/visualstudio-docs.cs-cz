---
title: Konkrétní požadavky na zabezpečení pro řešení Office
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 571b604b87fb7fac4e78c83a791c265d910fae94
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985585"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Konkrétní požadavky na zabezpečení pro řešení Office
  Funkce zabezpečení poskytované Microsoftem .NET Framework a systém Microsoft Office můžou pomáhat chránit vaše řešení pro Office proti možným bezpečnostním hrozbám. Toto téma vysvětluje některé z těchto hrozeb a poskytuje doporučení, která jim pomůžou s jejich ochranou. Obsahuje také informace o tom, jak systém Microsoft Office nastavení zabezpečení ovlivňují řešení Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>U důvěryhodného kódu se má změnit účel v novém škodlivém dokumentu.
 Útočník by mohl použít důvěryhodný kód, který je určen pro určitý účel, například stahování osobních údajů pro aplikaci pro zaměstnanost a jejich opětovné použití v jiném dokumentu, jako je například list. Kód neví, že původní dokument není spuštěný, a může otevřít jiné hrozby, jako je například odhalení osobních údajů nebo provádění kódu se zvýšenými oprávněními, pokud je otevře jiný uživatel. Případně může útočník změnit data v listu tak, že při odeslání do oběti se neočekávaně chová. Když změníte hodnoty, vzorce nebo prezentační charakteristiky listu propojeného s kódem, je možné, že uživatel se zlými úmysly útočí na jiného uživatele tím, že pošle změněný soubor. Uživatelé můžou taky získat přístup k informacím, které nemusejí zobrazit, úpravou hodnot v listu.

 Vzhledem k tomu, že umístění sestavení i umístění dokumentu musí mít dostatečný důkaz ke spuštění, nemůžete tento útok snadno připojit. Například dokumenty v přílohách e-mailu nebo na nedůvěryhodných intranetových serverech nemají dostatečná oprávnění ke spuštění.

 Aby bylo možné tento útok provést, musí být samotný kód napsán takovým způsobem, který umožňuje rozhodování na základě potenciálně nedůvěryhodných dat. Příkladem je vytvoření listu, který má skrytou buňku, která obsahuje název databázového serveru. Uživatel odešle list na stránku ASPX, která se pokusí připojit k tomuto serveru pomocí ověřování SQL a pevně zakódovaného hesla SA. Útočník by mohl nahradit obsah skryté buňky jiným názvem počítače a získat heslo SA. Chcete-li se tomuto problému vyhnout, nikdy nepoužívejte hesla pevného kódu a vždy kontrolujte ID serveru před přístupem k serveru pomocí interního seznamu serverů, u kterých je známo, že jsou dobré.

### <a name="recommendations"></a>Doporučit

- Vždy ověřte vstup a data, ať už pochází od uživatele, dokumentu, databáze, webové služby nebo jiného zdroje.

- Buďte opatrní při vystavování určitých typů funkčnosti, jako je například získání privilegovaných dat jménem uživatele a jeho umístění do nechráněného listu.

- V závislosti na typu aplikace může být vhodné ověřit, zda je původní dokument spuštěn před spuštěním libovolného kódu. Ověřte například, že je spuštěn z dokumentu uloženého v známém, zabezpečeném umístění.

- Může být vhodné zobrazit upozornění, když se dokument otevře, pokud aplikace provede jakékoli privilegované akce. Můžete například vytvořit úvodní obrazovku nebo úvodní dialogové okno s oznámením, že aplikace bude mít přístup k osobním údajům a že uživatel bude chtít pokračovat nebo zrušit. Pokud koncový uživatel získá takové upozornění z zdánlivě Innocent dokumentu, bude moci aplikaci ukončit, aby došlo k ohrožení zabezpečení.

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Kód je blokován ochranou modelu objektu aplikace Outlook.
 Systém Microsoft Office může omezit kód pomocí určitých vlastností, metod a objektů v objektovém modelu. Omezením přístupu k těmto objektům pomáhá aplikace Outlook zabránit e-mailovým červům a virům v používání modelu objektu pro škodlivé účely. Tato funkce zabezpečení je známá jako ochrana modelu objektu aplikace Outlook. Pokud se doplněk VSTO pokusí použít omezenou vlastnost nebo metodu, zatímco je zapnutá ochrana objektového modelu, Outlook zobrazí upozornění zabezpečení, které uživateli umožňuje operaci zastavit, nebo umožňuje uživateli udělit přístup k vlastnosti nebo metodě po omezenou dobu t. režim. Pokud uživatel operaci zastaví, doplňky VSTO pro Outlook vytvořené pomocí řešení Office v sadě Visual Studio vyvolají <xref:System.Runtime.InteropServices.COMException>.

 Ochrana objektového modelu může ovlivnit doplňky VSTO různými způsoby v závislosti na tom, jestli se aplikace Outlook používá se systémem Microsoft Exchange Server:

- Pokud se aplikace Outlook nepoužívá se serverem Exchange, může správce povolit nebo zakázat ochranu objektového modelu pro všechny doplňky VSTO v počítači.

- Pokud se aplikace Outlook používá se serverem Exchange, může správce povolit nebo zakázat ochranu objektového modelu pro všechny doplňky VSTO v počítači nebo může správce určit, že se některé doplňky VSTO můžou spustit, aniž by narazili na ochranu objektového modelu. Správci mohou také upravit chování ochrany objektového modelu pro určité oblasti objektového modelu. Správci můžou například automaticky povolit, aby doplňky VSTO odesílaly e-maily prostřednictvím kódu programu, i když je zapnutá ochrana objektového modelu.

  Od aplikace Outlook 2007 se chování ochrany objektového modelu změnilo, aby se zlepšila činnost vývojářů a uživatelů při zachování zabezpečení Outlooku. Další informace najdete v tématu [změny zabezpečení kódu v aplikaci Outlook 2007](/previous-versions/office/developer/office-2007/bb226709(v=office.12)).

### <a name="minimize-object-model-guard-warnings"></a>Minimalizovat upozornění ochrany objektového modelu
 Aby se zabránilo upozorněním na zabezpečení při použití omezených vlastností a metod, ujistěte se, že doplněk VSTO získá objekty Outlooku z pole `Application` třídy `ThisAddIn` ve vašem projektu. Další informace o tomto poli najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md).

 Ochranou modelu objektu mohou být důvěryhodné pouze objekty aplikace Outlook získané z tohoto objektu. Naproti tomu objekty, které jsou získány z nového objektu `Microsoft.Office.Interop.Outlook.Application` nejsou důvěryhodné a vlastnosti a metody s omezením budou generovat upozornění zabezpečení, pokud je povoleno ochrany objektového modelu.

 Následující příklad kódu zobrazí upozornění zabezpečení, pokud je povoleno ochrany objektového modelu. Vlastnost `To` třídy `Microsoft.Office.Interop.Outlook.MailItem` je omezená ochranou objektového modelu. Objekt `Microsoft.Office.Interop.Outlook.MailItem` je nedůvěryhodný, protože ho kód získá z `Microsoft.Office.Interop.Outlook.Application`, který je vytvořen pomocí operátoru **New** , namísto jeho získání z pole `Application`.

 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]

 Následující příklad kódu ukazuje, jak použít vlastnost omezit na objekt `Microsoft.Office.Interop.Outlook.MailItem`, který je důvěryhodný pro ochranu objektového modelu. Kód používá pole důvěryhodné `Application` k získání `Microsoft.Office.Interop.Outlook.MailItem`.

 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]

> [!NOTE]
> Pokud se aplikace Outlook používá se serverem Exchange, pak se při získání všech objektů Outlooku z `ThisAddIn.Application` nezaručuje, že váš doplněk VSTO bude mít přístup k celému objektovému modelu aplikace Outlook. Pokud například správce serveru Exchange nastaví Outlook tak, aby automaticky zamítl všechny pokusy o přístup k informacím o adrese pomocí objektového modelu aplikace Outlook, pak Outlook neumožní předchozímu příkladu kódu přistupovat k vlastnosti k, i když příklad kódu používá pole důvěryhodného `ThisAddIn.Application`.

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Určete, které doplňky se mají důvěřovat při používání Exchange.
 Pokud se aplikace Outlook používá se serverem Exchange, můžou správci určit, že se některé doplňky VSTO můžou spouštět bez toho, aby se narazí na ochranu objektového modelu. Doplňky VSTO pro Outlook vytvořené pomocí řešení Office v sadě Visual Studio nemůžou být důvěryhodné jednotlivě; můžou být jenom důvěryhodné jako skupina.

 Outlook důvěřuje doplňku VSTO na základě kódu hash knihovny DLL vstupního bodu doplňku VSTO. Všechny doplňky VSTO pro Outlook, které cílí na [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] používají stejnou knihovnu DLL vstupního bodu (*VSTOLoader. dll*). To znamená, že pokud správce důvěřuje jakémukoli doplňku VSTO, který cílí na [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] spustit, aniž by došlo k ochraně objektového modelu, pak všechny ostatní doplňky VSTO, které cílí na [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], jsou taky důvěryhodné. Další informace o tom, jak spustit konkrétní doplňky VSTO, aniž by došlo k ochraně objektového modelu, najdete v tématu [určení metody, kterou Outlook používá ke správě funkcí prevence virů](/previous-versions/office/office-2007-resource-kit/cc179194(v=office.12)).

## <a name="permission-changes-do-not-take-effect-immediately"></a>Změny oprávnění se projeví okamžitě.
 Pokud správce upraví oprávnění pro dokument nebo sestavení, musí uživatelé ukončit a znovu spustit všechny aplikace Office, aby se tyto změny vynutily.

 Další aplikace, které hostují aplikace systém Microsoft Office, můžou také zabránit vymáhání nových oprávnění. Pokud dojde ke změně zásad zabezpečení, uživatelé by měli ukončit všechny aplikace, které používají Office, Hosted nebo samostatně.

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Nastavení centra zabezpečení v systém Microsoft Office systému nemá vliv na doplňky nebo přizpůsobení na úrovni dokumentu
 Uživatelé můžou zabránit načítání doplňků VSTO nastavením možnosti v **Centru zabezpečení**. U doplňků a úprav na úrovni dokumentu vytvořených pomocí řešení Office v sadě Visual Studio však tato nastavení důvěryhodnosti neovlivní.

 Pokud uživatel zabrání načtení doplňků VSTO pomocí **centra zabezpečení**, následující typy doplňků VSTO se nenačte:

- Spravované a nespravované doplňky modelu COM VSTO.

- Spravované a nespravované inteligentní dokumenty.

- Spravované a nespravované doplňky VSTO pro automatizaci

- Spravované a nespravované datové komponenty v reálném čase.

  Následující postupy popisují, jak můžou uživatelé pomocí **centra zabezpečení** omezit načítání doplňků VSTO v Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a systém Microsoft Office 2010. Tyto postupy neovlivňují doplňky VSTO ani vlastní nastavení vytvořená pomocí vývojářských nástrojů Office v sadě Visual Studio.

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice_15_shortvstoincludesoffice-15-short-mdmd-applications"></a>Zakázání doplňků VSTO v aplikacích systém Microsoft Office 2010 a Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]

1. Klikněte na kartu **soubor** .

2. Klikněte na tlačítko **Možnosti** *ApplicationName* .

3. V podokně kategorie vyberte **Centrum zabezpečení**.

4. V podokně podrobností vyberte **Nastavení centra zabezpečení**.

5. V podokně kategorie vyberte možnost **Doplňky**.

6. V podokně podrobností vyberte možnost **vyžadovat, aby doplňky aplikací byly podepsány důvěryhodným vydavatelem** , nebo **zakažte všechny doplňky aplikací**.

## <a name="see-also"></a>Viz také:
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
