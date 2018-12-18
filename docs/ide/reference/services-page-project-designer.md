---
title: Stránka Služby, návrhář projektu
ms.date: 01/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba03b4aea25decef39983d203db12dfbedc516d9
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177016"
---
# <a name="services-page-project-designer"></a>Stránka Služby, návrhář projektu

Klientské aplikační služby nabízejí zjednodušený přístup ke [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] přihlášení, role a služby profilu v aplikacích Windows Forms a Windows Presentation Foundation (WPF). Můžete použít **služby** stránku **Návrháře projektu** povolení a konfigurace klientských aplikačních služeb pro váš projekt.

U klientských aplikačních služeb můžete použít centralizované serverové k ověřování uživatelů, určete každý uživatel přiřazenou roli nebo role a ukládání nastavení aplikace pro jednotlivé uživatele, které můžete sdílet přes síť. Další informace najdete v tématu [klientských aplikačních služeb](/dotnet/framework/common-client-technologies/client-application-services).

Pro přístup **služby** stránky, vyberte uzel projektu v **Průzkumníku řešení**a potom klikněte na **vlastnosti** na **projektu** nabídky. Když **Návrháře projektu** se zobrazí, klikněte na tlačítko **služby** kartu.

## <a name="task-list"></a>Seznam úloh

[Postupy: Konfigurace klientských aplikačních služeb](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

 **Konfigurace**

 Tento ovládací prvek není na této stránce upravovat. Popis tohoto ovládacího prvku, naleznete v tématu [stránka kompilovat, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) nebo [stránku sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platforma**

 Tento ovládací prvek není na této stránce upravovat. Popis tohoto ovládacího prvku, naleznete v tématu [stránka kompilovat, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) nebo [stránku sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Povolit klientské aplikační služby**

 Vyberte povolit klientské aplikační služby. Je nutné zadat umístění služby na **služby** stránku klientské aplikační služby.

 **Používat ověřování Windows**

 Označuje, že zprostředkovatel ověřování bude používat ověřování založené na Windows, to znamená, identity, které jsou součástí operačního systému Windows.

 **Ověřování pomocí formulářů**

 Označuje, že zprostředkovatel ověřování bude používat ověřování pomocí formulářů. To znamená, že vaše aplikace musí poskytovat uživatelského rozhraní pro přihlášení. Další informace najdete v tématu [postupy: implementace přihlášení uživatele u klientských aplikačních služeb](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).

 **Umístění služby ověřování**

 Použít pouze s ověřování pomocí formulářů. Určuje umístění ověřovací služby.

 **Volitelné: Přihlašovací údaje poskytovatele**

 Použít pouze s ověřování pomocí formulářů. Označuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> implementace, která se má zobrazit dialogové okno přihlášení, když vaše aplikace volá bude používat službu ověřování `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> metoda a předá prázdné řetězce nebo `null` parametrů. Když toto pole ponecháte prázdné, je nutné předat platné uživatelské jméno a heslo <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> metody. Jako název typu kvalifikovaného pro sestavení, je nutné zadat poskytovatele přihlašovacích údajů. Další informace najdete v tématu <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> a [názvy sestavení](/dotnet/framework/app-domains/assembly-names). Ve své nejjednodušší podobě vypadá podobně jako v následujícím příkladu představuje název typu kvalifikovaného pro sestavení: `MyNamespace.MyLoginClass, MyAssembly`

 **Umístění služby role**

 Určuje umístění služby rolí.

 **Nastavení webové služby umístění**

 Určuje umístění služby profilu (nastavení webu).

 **Pokročilé**

 Otevře [rozšířená nastavení pro dialogové okno služby](../../ide/reference/advanced-settings-for-services-dialog-box.md), což vám umožní potlačit výchozí chování. Například můžete použít toto dialogové okno zadat databázi pro offline úložiště namísto použití místního systému souborů. Další informace najdete v tématu [rozšířená nastavení pro dialogové okno služby](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Viz také:

- [Klientské aplikační služby](/dotnet/framework/common-client-technologies/client-application-services)
- [Dialogové okno Pokročilé nastavení služeb](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [Postupy: Konfigurace klientských aplikačních služeb](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [Stránka Kompilovat, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Stránka Sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
