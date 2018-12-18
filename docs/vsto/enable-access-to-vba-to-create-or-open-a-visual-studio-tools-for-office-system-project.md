---
title: Povolení přístupu k VBA vytvořit nebo otevřít nástrojů sady Visual Studio pro projekt systému Microsoft Office
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f17c4e1481e7f33034e16d1e60a285b25c6f8230
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448988"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Povolení přístupu k VBA vytvořit nebo otevřít nástrojů sady Visual Studio pro projekt systému Microsoft Office

Předtím, než můžete vytvořit nebo otevřít nástrojů sady Visual Studio pro projekt systému Microsoft Office je potřeba explicitně povolit přístup k jazyka Visual Basic pro aplikace (VBA) systému projektu v Microsoft Office.

 Přestože projektů jazyka Visual Basic pro aplikace nepoužívejte projekty vývoje aplikace Microsoft Office vyžadují přístup k jazyka Visual Basic pro aplikace (VBA) systému projektu v aplikaci Microsoft Office Word a Microsoft Office Excel. Podpora návrhu ovládacích prvků v projektech Visual Basic a C# závisí na Visual Basic pro aplikace systému projektu.

 Některé viry makra Microsoft Office se pokusí automatizovat Visual Basic pro aplikace systému projektu jako prostředek k šíření sami. Když povolíte přístup k jazyka Visual Basic pro aplikace systému projektu, odeberete ochrany, která pomáhá zabránit šíření makro virů. Normální – makro zabezpečení ale zůstává na místě, tak úroveň zabezpečení maker a seznam důvěryhodných vydavatelů, které udržují pro aplikace sady Office určí, zda všechny makro běží ve vašem počítači.

> [!NOTE]
> Vztahuje se pouze na vývojovém počítači. Počítače koncového uživatele, není nutné tuto možnost povolení spouštět řešení pro systém Office.

 Je důležité si uvědomit, že zakázání přístup k jazyka Visual Basic pro aplikace systému projektu na svůj vlastní není chráněn před viry, jednoduše pomáhá zastavit šíření na jiné dokumenty, pokud je počítač někdy stane napaden makra některé viry virů. Tato možnost je vypnuta ve výchozím nastavení jako další vrstvu ochrany pro počítače, ale jeho povolení neprovede váš počítač všechny náchylnější k viry pokud postupujete podle osvědčené postupy zabezpečení.

 Nejlepší ochrana proti virům je spuštění Office vysoká nebo velmi vysokou úroveň zabezpečení, pouze důvěřovat makra z ověřen, známé zdrojů, Office a udržovat přehled s opravy zabezpečení a pro vyhledávání virů.

 Další informace o chránit váš počítač před viry a další škodlivý kód, najdete v části [ http://www.microsoft.com/protect ](http://www.microsoft.com/protect).

 Můžete povolit nebo zakázat možnost **důvěřovat přístup k projektu jazyka Visual Basic** ručně.

 Pokud se zobrazí chyby VBA nebo COM, můžete opravit instalaci systému Office.

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Pokud chcete povolit nebo zakázat přístup k projekty Visual Basic

1. Klikněte **souboru** kartě.

2. Klikněte na tlačítko **možnosti**.

3. Klikněte na tlačítko **Centrum zabezpečení**a potom klikněte na **nastavení Centra zabezpečení**.

4. V **Centrum zabezpečení**, klikněte na tlačítko **makro nastavení**.

5. Zaškrtněte nebo zrušte zaškrtnutí políčka **důvěřovat přístup k modelu objektu projektu VBA** chcete povolit nebo zakázat přístup k projekty Visual Basic.

6. Click **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Pokud chcete povolit nebo zakázat přístup k projekty Visual Basic pomocí systému Microsoft Office 2007

1. Na **nástroje** nabídky v Word či Excel, přejděte na **makro**a potom klikněte na **zabezpečení**.

2. V **zabezpečení** dialogové okno, klikněte **důvěryhodných vydavatelů** kartě.

3. Vyberte, chcete-li povolit, nebo zrušte zakázat, **důvěřovat přístup k projektu jazyka Visual Basic**.

4. Click **OK**.

## <a name="to-set-your-office-macro-security-level"></a>Chcete-li nastavit úroveň zabezpečení Office – makro

1. Klikněte **souboru** kartě.

2. Klikněte na tlačítko **možnosti**.

3. Klikněte na tlačítko **Centrum zabezpečení**a potom klikněte na **nastavení Centra zabezpečení**.

4. V **Centrum zabezpečení**, klikněte na tlačítko **makro nastavení**.

5. V **makro nastavení** vyberte požadované nastavení.

6. Click **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Chcete-li nastavit úroveň zabezpečení maker Office pomocí systému Microsoft Office 2007

1. Na **nástroje** nabídky v Word či Excel, přejděte na **makro**a potom klikněte na **zabezpečení**.

2. Na **úroveň zabezpečení** , vyberte požadované nastavení.

    **Úroveň zabezpečení** karta obsahuje podrobnosti o jednotlivých úrovních. Další informace naleznete v tématu "Makro úrovně zabezpečení" v nápovědě sady Office.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Chcete-li nainstalovat VBA pomocí systému Microsoft Office 2007

1. V Ovládacích panelech spustit **přidat nebo odebrat programy** nebo **programy a funkce**.

2. Vyberte v Office **aktuálně nainstalované programy** seznamu.

3. Klikněte na tlačítko **změnu**.

4. Vyberte **přidat nebo odebrat součásti**a potom klikněte na **pokračovat**.

5. Vyberte **zvolit vlastní aplikace**a potom klikněte na **Další**.

6. Rozbalte položku **sdílené součásti sady Office** v **zvolte možnosti aktualizace pro aplikace a nástroje** seznamu.

7. Otevřete rozevírací nabídce vedle položky **Visual Basic pro aplikace**a potom klikněte na **spouštět z tohoto počítače**.

8. Klikněte na tlačítko **pokračovat**.

9. Klikněte na tlačítko **Zavřít**.

## <a name="to-repair-your-installation-of-office"></a>Chcete-li opravit instalaci systému Office

1. V Ovládacích panelech spustit **přidat nebo odebrat programy** nebo **programy a funkce**.

2. Vyberte verzi systému Office v **aktuálně nainstalované programy** seznamu.

3. Klikněte na tlačítko **změnu**.

4. Vyberte **přeinstalovat nebo opravit**a potom klikněte na **Další**.

5. Vyberte **zjistit a opravit chyby v instalaci Office**a potom klikněte na **nainstalovat**.

## <a name="see-also"></a>Viz také

 [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)