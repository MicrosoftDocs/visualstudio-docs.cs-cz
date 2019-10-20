---
title: Dialogové okno Upřesnit nastavení pro služby | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a021475df1ade9bb6220612aad666d503c19cb8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651719"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Dialogové okno Pokročilé nastavení služeb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Klientské aplikační služby poskytují zjednodušený přístup k [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] přihlášení, rolí a profilové služby z aplikací model Windows Forms a Windows Presentation Foundation (WPF). Ke konfiguraci klientských aplikačních služeb můžete použít stránku **služby** v **Návrháři projektu** . Další informace o stránce **služby** naleznete na [stránce služby, Návrhář projektu](../../ide/reference/services-page-project-designer.md).

 Pomocí dialogového okna **Upřesnit nastavení služeb** stránky **služby** v **Návrháři projektu** můžete nakonfigurovat upřesňující nastavení pro klientské aplikační služby. Pomocí těchto nastavení můžete přepsat některá výchozí chování aplikační služby a povolit tak méně běžných scénářů. Další informace najdete v tématu [aplikační služby klienta](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).

 Chcete-li získat přístup k dialogovému oknu **Upřesnit nastavení služeb** , vyberte uzel projektu v **Průzkumník řešení**a potom klikněte na tlačítko **vlastnosti** v nabídce **projekt** . Když se zobrazí **Návrhář projektu** , klikněte na kartu **služby** a pak klikněte na tlačítko **Upřesnit** . Toto tlačítko bude zakázáno, dokud nepovolíte klientské aplikační služby.

## <a name="task-list"></a>Seznam úkolů
 [Postupy: Konfigurace klientských aplikačních služeb](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)

 [Postupy: práce v režimu offline pomocí Aplikační služby klienta](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Uložit hodnotu hash hesla lokálně pro povolení offline přihlášení** Určuje, zda bude zašifrovaná forma hesla uživatele ukládána do mezipaměti, aby se uživatel mohl přihlásit, když je aplikace v režimu offline. Další informace naleznete v tématu [How to: Work offline with aplikační služby klienta](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38). Tato možnost je vybrána ve výchozím nastavení.

 **Vyžadovat, aby se uživatelé přihlásili znovu vždy, když vyprší platnost souboru cookie serveru** Určuje, jestli má být dřív ověřený uživatel znovu ověřený, když vaše aplikace přistupuje k rolím nebo službě profilů a vypršela platnost souboru cookie pro ověření serveru. Tuto možnost vyberte, pokud chcete odepřít přístup k aplikačním službám a po vypršení platnosti souboru cookie vyžadovat explicitní opakované ověření. To je užitečné pro aplikace nasazené ve veřejných umístěních, aby se zajistilo, že uživatelé, kteří aplikaci spouštějí po použití, se nebudou nadále ověřovat po neomezenou dobu. Tato možnost je ve výchozím nastavení prázdná.

 **Časový limit mezipaměti služby role** Určuje dobu, po kterou bude zprostředkovatel rolí klienta místo přístupu ke službě rolí používat hodnoty role v mezipaměti. Nastavte tento časový interval na malou hodnotu, pokud se role často aktualizují, nebo na větší hodnotu, když se role aktualizují zřídka. Výchozí hodnota je jeden den.

 Zprostředkovatel rolí přistupuje k hodnotám role v mezipaměti nebo službě rolí při volání metody <xref:System.Web.Security.RolePrincipal.IsInRole%2A>. Pro programové vymazání mezipaměti a vynucení této metody pro přístup ke vzdálené službě volejte metodu <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>.

 **Použít vlastní připojovací řetězec** Určuje, jestli budou poskytovatelé služeb klienta používat vlastní úložiště dat pro místní mezipaměť. Ve výchozím nastavení budou poskytovatelé služeb používat místní systém souborů pro mezipaměť. Výběrem této možnosti se automaticky naplní textové pole výchozím připojovacím řetězcem. Můžete ponechat výchozí připojovací řetězec pro automatické generování a používání databáze edice SQL Server Compact, nebo můžete zadat připojovací řetězec do existující databáze SQL Server. Další informace naleznete v tématu [How to: configure aplikační služby klienta](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8). Tato možnost je ve výchozím nastavení prázdná.

## <a name="see-also"></a>Viz také
 Stránka [klientské aplikační služby](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e) [Services, Návrhář projektu](../../ide/reference/services-page-project-designer.md) [Postupy: Konfigurace klienta aplikační služby](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8) [postupy: práce offline s klientským aplikační služby](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)
