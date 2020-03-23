---
title: Dialogové okno Pokročilé nastavení služeb
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 967e99102f3b88e82a5466e7ce8d2cac2412d286
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585675"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Dialogové okno Pokročilé nastavení služeb
Klientské aplikační služby [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] poskytují zjednodušený přístup ke službám přihlášení, rolí a profilů z aplikací Windows Forms a Windows Presentation Foundation (WPF). Stránku **Služby** v **Návrháři projektu** můžete použít ke konfiguraci klientských aplikačních služeb. Další informace o stránce **Služby** naleznete na [stránce Services Page, Project Designer](../../ide/reference/services-page-project-designer.md).

Pomocí dialogového okna **Upřesnit nastavení služeb** na stránce **Služby** v **Návrháři projektu** nakonfigurujte upřesňující nastavení pro služby klientských aplikací. Pomocí těchto nastavení můžete přepsat některé výchozí chování aplikační služby povolit méně běžné scénáře. Další informace naleznete [v tématu Client Application Services](/dotnet/framework/common-client-technologies/client-application-services).

Chcete-li získat přístup k dialogovému oknu **Upřesnit nastavení služeb,** vyberte uzel projektu v **Průzkumníku řešení**a v nabídce **Projekt** klepněte na **příkaz Vlastnosti.** Po zobrazení **Návrháře projektů** klikněte na kartu **Služby** a potom klikněte na tlačítko **Upřesnit.** Toto tlačítko bude zakázáno, dokud nepovolíte služby klientských aplikací.

## <a name="task-list"></a>Seznam úkolů

- [Postupy: Konfigurace klientských aplikačních služeb](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

 **Uložit haštejnou hašiš hesla místně pro povolení offline přihlášení** Určuje, zda bude šifrovaná forma hesla uživatele uložena do mezipaměti místně, aby se uživatel mohl přihlásit, když je aplikace v režimu offline. Tato možnost je ve výchozím nastavení zaškrtnutá.

 **Vyžadovat, aby se uživatelé znovu přihlásili při vypršení platnosti souboru cookie serveru** Určuje, zda budou dříve ověření uživatelé automaticky znovu ověřeni, když aplikace přistupuje ke službě rolí nebo profilu a vypršela platnost ověřovacího souboru serveru. Tuto možnost vyberte, chcete-li odepřít přístup k aplikačním službám a vyžadovat explicitní opětovné ověření po vypršení platnosti souboru cookie. To je užitečné pro aplikace nasazené ve veřejných umístěních a ujistěte se, že uživatelé, kteří opustí aplikaci spuštěnou po použití, nezůstanou ověřeni po neomezenou dobu. Tato možnost je ve výchozím nastavení vymazána.

 **Časový čas mezipaměti služby role** Určuje dobu, po kterou bude poskytovatel role klienta používat hodnoty rolí uložené v mezipaměti namísto přístupu ke službě rolí. Nastavte tento časový interval na malou hodnotu, pokud jsou role často aktualizovány, nebo na větší hodnotu, když jsou role aktualizovány zřídka. Výchozí hodnota je jeden den.

Zprostředkovatel role přistupuje k hodnotám rolí v <xref:System.Web.Security.RolePrincipal.IsInRole%2A> mezipaměti nebo službě rolí při volání metody. Chcete-li programově vymazat mezipaměť a vynutit tuto <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> metodu pro přístup ke vzdálené službě, volání metody.

 **Použití vlastního připojovacího řetězce** Určuje, zda budou poskytovatelé klientských služeb používat vlastní úložiště dat pro místní mezipaměť. Ve výchozím nastavení budou poskytovatelé služeb používat pro mezipaměť místní systém souborů. Výběrem této možnosti se automaticky naplní textové pole výchozím připojovacím řetězcem. Můžete zachovat výchozí připojovací řetězec pro automatické generování a použití databáze SQL Server Compact Edition nebo můžete zadat připojovací řetězec k existující databázi serveru SQL Server. Další informace naleznete v [tématu How to: Configure Client Application Services](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services). Tato možnost je ve výchozím nastavení vymazána.

## <a name="see-also"></a>Viz také

- [Klientské aplikační služby](/dotnet/framework/common-client-technologies/client-application-services)
- [Stránka Služby, Návrhář projektu](../../ide/reference/services-page-project-designer.md)
- [Postupy: Konfigurace klientských aplikačních služeb](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
