---
title: Stránka Služby, návrhář projektu
description: Naučte se používat stránku služeb Návrháře projektu k povolení a konfiguraci klientských aplikačních služeb pro svůj projekt.
ms.custom: SEO-VS-2020
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c286dbd632e09a9a9c2c2b62ac2002f2e48f283
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560795"
---
# <a name="services-page-project-designer"></a>Stránka Služby, návrhář projektu

Klientské aplikační služby poskytují zjednodušený přístup k [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] přihlašování, rolím a profilovým službám z aplikací model Windows Forms a Windows Presentation Foundation (WPF). Stránku **služby** **Návrháře projektu** můžete použít k povolení a konfiguraci klientských aplikačních služeb pro svůj projekt.

Pomocí klientských aplikačních služeb můžete pomocí centralizovaného serveru ověřovat uživatele, určit role nebo role přiřazené jednotlivým uživatelům a ukládat nastavení aplikací pro jednotlivé uživatele, která můžete sdílet přes síť. Další informace najdete v tématu [aplikační služby klienta](/dotnet/framework/common-client-technologies/client-application-services).

Chcete-li získat přístup ke stránce **služby** , vyberte uzel projektu v **Průzkumník řešení** a potom klikněte na tlačítko **vlastnosti** v nabídce **projekt** . Když se zobrazí **Návrhář projektu** , klikněte na kartu **služby** .

## <a name="task-list"></a>Seznam úkolů

[Postupy: Konfigurace klientských aplikačních služeb](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

 **Konfigurace**

Tento ovládací prvek není na této stránce možné upravovat. Popis tohoto ovládacího prvku naleznete v tématu [Kompilovat stránku, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) nebo [Stránka sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platforma**

Tento ovládací prvek není na této stránce možné upravovat. Popis tohoto ovládacího prvku naleznete v tématu [Kompilovat stránku, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) nebo [Stránka sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Povolit klientské aplikační služby**

Tuto možnost vyberte, pokud chcete povolit klientské aplikační služby. Aby bylo možné používat klientské aplikační služby, je nutné zadat umístění služby na stránce **služby** .

 **Použít ověřování systému Windows**

Označuje, že zprostředkovatel ověřování bude používat ověřování založené na systému Windows, to znamená identitu poskytovanou operačním systémem Windows.

 **Použití ověřování pomocí formulářů**

Označuje, že zprostředkovatel ověřování bude používat ověřování pomocí formulářů. To znamená, že aplikace musí poskytnout uživatelské rozhraní pro přihlášení. Další informace najdete v tématu [Postup: implementace přihlášení uživatele pomocí aplikační služby klienta](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).

 **Umístění ověřovací služby**

Používá se pouze s ověřováním pomocí formulářů. Určuje umístění ověřovací služby.

 **Volitelné: Poskytovatel pověření**

Používá se pouze s ověřováním pomocí formulářů. Označuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> implementaci, kterou bude služba ověřování používat k zobrazení přihlašovacího dialogového okna, když vaše aplikace volá `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> metodu a předá prázdné řetězce nebo `null` parametry. Pokud toto pole necháte prázdné, musíte do metody předat platné uživatelské jméno a heslo <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> . Je nutné zadat poskytovatele pověření jako název typu kvalifikovaného pro sestavení. Další informace naleznete v tématu <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> a [názvy sestavení](/dotnet/framework/app-domains/assembly-names). V nejjednodušším tvaru název kvalifikovaného typu sestavení vypadá podobně jako v následujícím příkladu: `MyNamespace.MyLoginClass, MyAssembly`

 **Umístění služby rolí**

Určuje umístění služby rolí.

 **Umístění služby webového nastavení**

Určuje umístění služby Profile (webové nastavení).

 **Pokročilý**

Otevře [dialogové okno Upřesnit nastavení pro služby](../../ide/reference/advanced-settings-for-services-dialog-box.md), které můžete použít k přepsání výchozího chování. Toto dialogové okno můžete například použít k určení databáze pro úložiště offline místo použití místního systému souborů. Další informace najdete v tématu [Pokročilá nastavení pro služby v dialogovém okně](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Viz také:

- [Klientské aplikační služby](/dotnet/framework/common-client-technologies/client-application-services)
- [Dialogové okno Pokročilé nastavení služeb](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [Postupy: Konfigurace klientských aplikačních služeb](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [Stránka Kompilovat, návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Stránka Sestavení, návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
