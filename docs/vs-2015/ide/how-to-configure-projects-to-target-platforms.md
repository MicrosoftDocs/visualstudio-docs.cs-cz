---
title: 'Postupy: Konfigurace projektů pro cílové platformy | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4e2b39aa13316b1b9ca47c5587ffabf6f6a14e68
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843051"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Postupy: Konfigurace projektů pro cílové platformy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Umožňuje nastavit vašich aplikací na různých platformách, včetně 64bitových platforem. Další informace o 64bitové platformě podporují v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], naleznete v tématu [64bitové aplikace](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>Cílení na platformy s Configuration Managerem  
 **Nástroje Configuration Manager** poskytuje způsob, jak můžete rychle přidat novou platformu k cíli s projektem. Pokud vyberete některou z platforem součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], dojde k úpravě vlastností pro váš projekt k sestavení projektu pro vybranou platformu.  
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Ke konfiguraci projektu cílit na 64bitové platformě  
  
1. V panelu nabídky zvolte **sestavení**, **nástroje Configuration Manager**.  
  
2. V **platformou aktivního řešení** seznamu, zvolte 64bitovou platformu pro řešení do cíle a klikněte na tlačítko **Zavřít** tlačítko.  
  
   1.  Pokud se nezobrazí platforma, která chcete v **platformou aktivního řešení** klikněte na položku **nový**.  
  
        **Nová platforma řešení** zobrazí se dialogové okno.  
  
   2.  V **zadejte nebo vyberte novou platformu** klikněte na položku **x64**.  
  
       > [!NOTE]
       >  Pokud vaše konfigurace zadejte nový název, bude pravděpodobně nutné upravit nastavení v **Návrháře projektu** pro zaměření na správnou platformu.  
  
   3.  Pokud chcete tato nastavení zkopírovat z aktuální konfiguraci platformy, vyberte jej a klikněte na tlačítko **OK** tlačítko.  
  
   Jsou aktualizovány vlastnosti pro všechny projekty, které se zaměřují 64bitové platformě a optimalizují se další sestavení projektu pro 64bitové platformy.  
  
## <a name="targeting-platforms-in-the-project-designer"></a>Cílení na platformy v Návrháři projektu  
 Návrhář projektu také poskytuje způsob, jak určené pro různé platformy s projektem. Pokud vyberete některou z platforem zahrnuté v seznamu **nová platforma řešení** dialogové okno pro vaše řešení nebude fungovat, můžete vytvořit vlastní název a upravte nastavení v **Návrhář projektu**  pro zaměření na správnou platformu.  
  
 Provedení tohoto úkolu se liší v závislosti na programovacím jazyku, který používáte. V následujících tématech pro další informace:  
  
-   Pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektů, naleznete v tématu [/Platform (Visual Basic)](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).  
  
-   Pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektů, naleznete v tématu [stránku sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
-   Pro [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektů, naleznete v tématu [/CLR (kompilace Common Language Runtime)](http://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
## <a name="see-also"></a>Viz také  
 [Principy platforem sestavení](../ide/understanding-build-platforms.md)   
 [/ Platform (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04)   
 [64bitové aplikace](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Podpora pro 64bitové integrované vývojové prostředí sady Visual Studio](../ide/visual-studio-ide-64-bit-support.md)



