---
title: Stránka služby, Návrhář projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 11e1cd997c76974e7b4b8771c0579c175469eca6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665477"
---
# <a name="services-page-project-designer"></a>Stránka Služby, návrhář projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Klientské aplikační služby poskytují zjednodušený přístup k [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] přihlášení, rolí a profilové služby z aplikací model Windows Forms a Windows Presentation Foundation (WPF). Stránku **služby** **Návrháře projektu** můžete použít k povolení a konfiguraci klientských aplikačních služeb pro svůj projekt.

 Pomocí klientských aplikačních služeb můžete pomocí centralizovaného serveru ověřovat uživatele, určit role nebo role přiřazené jednotlivým uživatelům a ukládat nastavení aplikací pro jednotlivé uživatele, která můžete sdílet přes síť. Další informace najdete v tématu [aplikační služby klienta](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).

 Chcete-li získat přístup ke stránce **služby** , vyberte uzel projektu v **Průzkumník řešení**a potom klikněte na tlačítko **vlastnosti** v nabídce **projekt** . Když se zobrazí **Návrhář projektu** , klikněte na kartu **služby** .

> [!NOTE]
> Klientské aplikační služby vyžadují plnou verzi .NET Framework a nejsou podporovány v profilech klienta .NET Framework. Pokud není zaškrtnuté políčko **Povolit klientské aplikační služby** , ověřte, zda je **Cílová architektura** nastavena na .NET Framework 3,5 nebo novější. Chcete-li zobrazit **cílové nastavení rozhraní .NET Framework** C#, otevřete Návrháře projektu a poté klikněte na stránku **aplikace** . Chcete-li zobrazit nastavení **cílové architektury** v Visual Basic, otevřete Návrháře projektu, klikněte na stránku **kompilovat** a pak klikněte na možnost **Pokročilé možnosti kompilace**.

## <a name="task-list"></a>Seznam úkolů
 [Postupy: Konfigurace klientských aplikačních služeb](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Konfigurace** Tento ovládací prvek není na této stránce možné upravovat. Popis tohoto ovládacího prvku naleznete v tématu [Kompilovat stránku, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) nebo [Stránka sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platforma** Tento ovládací prvek není na této stránce možné upravovat. Popis tohoto ovládacího prvku naleznete v tématu [Kompilovat stránku, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) nebo [Stránka sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Povolit klientské aplikační služby** Tuto možnost vyberte, pokud chcete povolit klientské aplikační služby. Aby bylo možné používat klientské aplikační služby, je nutné zadat umístění služby na stránce **služby** .

 **Použít ověřování systému Windows** Označuje, že zprostředkovatel ověřování bude používat ověřování založené na systému Windows, to znamená identitu poskytovanou operačním systémem Windows.

 **Použití ověřování pomocí formulářů** Označuje, že zprostředkovatel ověřování bude používat ověřování pomocí formulářů. To znamená, že aplikace musí poskytnout uživatelské rozhraní pro přihlášení. Další informace najdete v tématu [Postup: implementace přihlášení uživatele pomocí aplikační služby klienta](https://msdn.microsoft.com/library/5431a671-eb02-4e18-a651-24764fccec9a).

 **Umístění ověřovací služby** Používá se pouze s ověřováním pomocí formulářů. Určuje umístění ověřovací služby.

 **Volitelné: Poskytovatel pověření** Používá se pouze s ověřováním pomocí formulářů. Určuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> implementaci, kterou bude ověřovací služba používat k zobrazení přihlašovacího dialogového okna, když vaše aplikace volá metodu `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> a předá prázdné řetězce nebo `null` pro parametry. Pokud toto pole necháte prázdné, musíte do metody <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> předat platné uživatelské jméno a heslo. Je nutné zadat poskytovatele pověření jako název typu kvalifikovaného pro sestavení. Další informace naleznete v tématu <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> a [názvy sestavení](https://msdn.microsoft.com/library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e). V nejjednodušším tvaru název kvalifikovaného typu sestavení vypadá podobně jako v následujícím příkladu: `MyNamespace.MyLoginClass, MyAssembly`

 **Umístění služby rolí** Určuje umístění služby rolí.

 **Umístění služby webového nastavení** Určuje umístění služby Profile (webové nastavení).

 **Rozšířené možnosti** Otevře [dialogové okno Upřesnit nastavení pro služby](../../ide/reference/advanced-settings-for-services-dialog-box.md), které můžete použít k přepsání výchozího chování. Toto dialogové okno můžete například použít k určení databáze pro úložiště offline místo použití místního systému souborů. Další informace najdete v tématu [Pokročilá nastavení pro služby v dialogovém okně](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Viz také
 Dialogové okno [klient aplikační služby](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e) [Upřesnit nastavení pro služby](../../ide/reference/advanced-settings-for-services-dialog-box.md) [Postup: Konfigurace](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8) stránky pro kompilaci aplikační služby klienta, stránky sestavení [Návrháře projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) [, Návrháře projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md) [Úvod do Návrháře projektu](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)
