---
title: 'Postupy: Konfigurace projektů pro cílové platformy'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2152f90d244ed283250bf8ea6a42a39b545f9c09
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847978"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Postupy: Konfigurace projektů pro cílové platformy

Visual Studio umožňuje nastavení aplikací na různých platformách, včetně 64bitových platforem. Další informace o podpoře platforem 64-bit v sadě Visual Studio najdete v tématu [64bitové aplikace](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Cílové platformy s Configuration Managerem

**Nástroje Configuration Manager** poskytuje způsob, jak můžete rychle přidat novou platformu k cíli s projektem. Pokud vyberete některou z platforem, které jsou součástí sady Visual Studio, úpravě vlastností pro váš projekt k sestavení projektu pro vybranou platformu.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Ke konfiguraci projektu cílit na 64bitové platformě

1.  V panelu nabídky zvolte **sestavení** > **nástroje Configuration Manager**.

2.  V **platformou aktivního řešení** seznamu, zvolte 64bitovou platformu pro řešení do cíle a klikněte na tlačítko **Zavřít** tlačítko.

    1.  Pokud se nezobrazí platforma, která chcete v **platformou aktivního řešení** klikněte na položku **nový**.

         **Nová platforma řešení** zobrazí se dialogové okno.

    2.  V **zadejte nebo vyberte novou platformu** klikněte na položku **x64**.

        > [!NOTE]
        >  Pokud vaše konfigurace zadejte nový název, bude pravděpodobně nutné upravit nastavení v **Návrháře projektu** pro zaměření na správnou platformu.

    3.  Pokud chcete tato nastavení zkopírovat z aktuální konfiguraci platformy, vyberte jej a klikněte na tlačítko **OK** tlačítko.

Jsou aktualizovány vlastnosti pro všechny projekty, které se zaměřují 64bitové platformě a optimalizují se další sestavení projektu pro 64bitové platformy.

## <a name="target-platforms-in-the-project-designer"></a>Cílové platformy v Návrháři projektu

**Návrháře projektu** také poskytuje způsob, jak určené pro různé platformy s projektem. Pokud vyberete některou z platforem zahrnuté v seznamu **nová platforma řešení** dialogové okno pro vaše řešení nebude fungovat, můžete vytvořit vlastní název a upravte nastavení v **Návrhář projektu**  pro zaměření na správnou platformu.

Provedení tohoto úkolu se liší v závislosti na programovacím jazyku, který používáte. V následujících tématech pro další informace:

- Pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektů, naleznete v tématu [/Platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektů, naleznete v tématu [stránka sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Pro [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektů, naleznete v tématu [/CLR (kompilace modulu Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="see-also"></a>Viz také:

- [Principy platforem sestavení](../ide/understanding-build-platforms.md)
- [/ Platform (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64bitové aplikace](/dotnet/framework/64-bit-apps)
- [Podpora v sadě Visual Studio IDE 64-Bit](../ide/visual-studio-ide-64-bit-support.md)
