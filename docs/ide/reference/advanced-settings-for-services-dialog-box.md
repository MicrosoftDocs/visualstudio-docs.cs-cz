---
title: Dialogové okno Pokročilé nastavení služeb
description: Naučte se používat funkce Rozšířené nastavení pro služby ke konfiguraci upřesňujících nastavení pro klientské aplikační služby.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b705042f7713b2571e391801c4a1d29734a031bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969799"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Dialogové okno Pokročilé nastavení služeb
Klientské aplikační služby poskytují zjednodušený přístup k [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] přihlašování, rolím a profilovým službám z aplikací model Windows Forms a Windows Presentation Foundation (WPF). Ke konfiguraci klientských aplikačních služeb můžete použít stránku **služby** v **Návrháři projektu** . Další informace o stránce **služby** naleznete na [stránce služby, Návrhář projektu](../../ide/reference/services-page-project-designer.md).

Pomocí dialogového okna **Upřesnit nastavení služeb** stránky **služby** v **Návrháři projektu** můžete nakonfigurovat upřesňující nastavení pro klientské aplikační služby. Pomocí těchto nastavení můžete přepsat některá výchozí chování aplikační služby a povolit tak méně běžných scénářů. Další informace najdete v tématu [aplikační služby klienta](/dotnet/framework/common-client-technologies/client-application-services).

Chcete-li získat přístup k dialogovému oknu **Upřesnit nastavení služeb** , vyberte uzel projektu v **Průzkumník řešení** a potom klikněte na tlačítko **vlastnosti** v nabídce **projekt** . Když se zobrazí **Návrhář projektu** , klikněte na kartu **služby** a pak klikněte na tlačítko **Upřesnit** . Toto tlačítko bude zakázáno, dokud nepovolíte klientské aplikační služby.

## <a name="task-list"></a>Seznam úkolů

- [Postupy: Konfigurace klientských aplikačních služeb](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

 **Uložit hodnotu hash hesla lokálně pro povolení offline přihlášení** Určuje, zda bude zašifrovaná forma hesla uživatele ukládána do mezipaměti, aby se uživatel mohl přihlásit, když je aplikace v režimu offline. Tato možnost je ve výchozím nastavení zaškrtnutá.

 **Vyžadovat, aby se uživatelé přihlásili znovu vždy, když vyprší platnost souboru cookie serveru** Určuje, jestli má být dřív ověřený uživatel znovu ověřený, když vaše aplikace přistupuje k rolím nebo službě profilů a vypršela platnost souboru cookie pro ověření serveru. Tuto možnost vyberte, pokud chcete odepřít přístup k aplikačním službám a po vypršení platnosti souboru cookie vyžadovat explicitní opakované ověření. To je užitečné pro aplikace nasazené ve veřejných umístěních, aby se zajistilo, že uživatelé, kteří aplikaci spouštějí po použití, se nebudou nadále ověřovat po neomezenou dobu. Tato možnost je ve výchozím nastavení prázdná.

 **Časový limit mezipaměti služby role** Určuje dobu, po kterou bude zprostředkovatel rolí klienta místo přístupu ke službě rolí používat hodnoty role v mezipaměti. Nastavte tento časový interval na malou hodnotu, pokud se role často aktualizují, nebo na větší hodnotu, když se role aktualizují zřídka. Výchozí hodnota je jeden den.

Zprostředkovatel rolí přistupuje k hodnotám role v mezipaměti nebo službě rolí při volání <xref:System.Web.Security.RolePrincipal.IsInRole%2A> metody. Pro programové vymazání mezipaměti a vynucení této metody pro přístup ke vzdálené službě volejte <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> metodu.

 **Použít vlastní připojovací řetězec** Určuje, jestli budou poskytovatelé služeb klienta používat vlastní úložiště dat pro místní mezipaměť. Ve výchozím nastavení budou poskytovatelé služeb používat místní systém souborů pro mezipaměť. Výběrem této možnosti se automaticky naplní textové pole výchozím připojovacím řetězcem. Můžete ponechat výchozí připojovací řetězec pro automatické generování a používání databáze edice SQL Server Compact, nebo můžete zadat připojovací řetězec do existující databáze SQL Server. Další informace naleznete v tématu [How to: configure aplikační služby klienta](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services). Tato možnost je ve výchozím nastavení prázdná.

## <a name="see-also"></a>Viz také

- [Klientské aplikační služby](/dotnet/framework/common-client-technologies/client-application-services)
- [Stránka Služby, návrhář projektu](../../ide/reference/services-page-project-designer.md)
- [Postupy: Konfigurace klientských aplikačních služeb](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
