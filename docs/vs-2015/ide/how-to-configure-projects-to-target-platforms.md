---
title: 'Postupy: konfigurace projektů pro cílové platformy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6ba899fd1b17fa5a82c64d5c5e44e67f0d5eb97
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668192"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Postupy: Konfigurace projektů pro cílové platformy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vám umožní nastavit vaše aplikace na jiné platformy, včetně 64-bitových platforem. Další informace o podpoře 64 bitových platforem v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] naleznete v tématu [64-bitové aplikace](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).

## <a name="targeting-platforms-with-the-configuration-manager"></a>Cílení platforem pomocí Configuration Manager
 **Configuration Manager** poskytuje způsob, jak rychle přidat novou platformu pro cílení na váš projekt. Pokud vyberete jednu z platforem, které jsou součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vlastnosti projektu se upraví a sestaví projekt pro vybranou platformu.

#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Konfigurace projektu pro cílení na 64 platformu

1. Na panelu nabídek vyberte možnost **sestavit**, **Configuration Manager**.

2. V seznamu **Aktivní platforma řešení** zvolte 64 platformu pro cílové řešení a pak klikněte na tlačítko **Zavřít** .

   1. Pokud se požadovaná platforma nezobrazí v seznamu **Aktivní platforma řešení** , vyberte možnost **nové**.

        Zobrazí se dialogové okno **Nová platforma řešení** .

   2. V rozevíracím seznamu **Typ vyberte Nová platforma** a zvolte možnost **x64**.

       > [!NOTE]
       > Pokud vaší konfiguraci přiřadíte nový název, může být nutné upravit nastavení v **Návrháři projektu** , aby se zacíleno na správnou platformu.

   3. Pokud chcete zkopírovat nastavení z aktuální konfigurace platformy, vyberte ji a pak klikněte na tlačítko **OK** .

   Vlastnosti pro všechny projekty, které cílí na 64, jsou aktualizovány a další sestavení projektu bude optimalizováno pro 64-bitové platformy.

## <a name="targeting-platforms-in-the-project-designer"></a>Cílení na platformy v Návrháři projektu
 Návrhář projektu také poskytuje způsob, jak cílit na různé platformy s vaším projektem. Pokud výběr jedné z platforem zahrnutých v seznamu v dialogovém okně **Nová platforma řešení** nefunguje pro vaše řešení, můžete vytvořit vlastní název konfigurace a upravit nastavení v **Návrháři projektu** , abyste mohli cílit na správnou platformu. .

 Provádění tohoto úkolu se liší v závislosti na programovacím jazyku, který používáte. Další informace najdete na následujících odkazech:

- @No__t_0 projektů naleznete v tématu [/Platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).

- Pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekty, viz [Stránka sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Pro [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projekty naleznete v tématu [/CLR (Common Language Runtime Compilation)](https://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).

## <a name="see-also"></a>Viz také
 [Porozumění platformám buildu](../ide/understanding-build-platforms.md) [/PlatformC# (možnosti kompilátoru)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04) [64-bitových aplikací](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181) sady [Visual Studio IDE 64-bitová podpora](../ide/visual-studio-ide-64-bit-support.md)
