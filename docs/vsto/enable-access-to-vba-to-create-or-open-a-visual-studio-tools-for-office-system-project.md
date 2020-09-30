---
title: Přístup k aplikaci VBA k vytvoření nebo otevření projektu systému VSTO
titleSuffix: ''
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
ms.custom: seodec18
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71e30a89bdf8547eab9ed9c51b07c49e014b7302
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584856"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Povolení přístupu k jazyku VBA pro vytvoření nebo otevření Visual Studio Tools pro projekt systém Microsoft Office systému

Musíte explicitně povolit přístup k systému projektu jazyk Visual Basic for Application (VBA) v systém Microsoft Office předtím, než budete moci vytvořit nebo otevřít Visual Studio Tools pro systémový projekt systém Microsoft Office.

 Systém Microsoft Office vývojové projekty vyžadují přístup k systému projektu jazyk Visual Basic for Application (VBA) v systém Microsoft Office Word a systém Microsoft Office Excel, i když projekty nepoužívají jazyk Visual Basic for Application. Podpora ovládacích prvků v době návrhu v projektech Visual Basic i C# závisí na jazyk Visual Basic for Application systém projektu.

 Některé systém Microsoft Office makro se snaží automatizovat jazyk Visual Basic for Application projektový systém jako prostředek k rozšíření samotného. Povolením přístupu do systému jazyk Visual Basic for Applicationho projektu odeberete ochranu, která pomáhá zabránit šíření virů v makrech. Avšak normální zabezpečení maker zůstává zachováno, takže úroveň zabezpečení makra a seznam důvěryhodných vydavatelů, které udržujete pro aplikace sady Office, určí, zda je v počítači spuštěno jakékoli makro.

> [!NOTE]
> To platí jenom pro vývojový počítač. Počítače koncového uživatele tuto možnost nepotřebují ke spouštění řešení pro Office.

 Je důležité si uvědomit, že zakázání přístupu k systému projektu jazyk Visual Basic for Application sám o sobě nebude chránit před viry, ale jednoduše pomůže zastavit rozšiřování některých virů do jiných dokumentů, pokud se Váš počítač někdy stane napadený virem makra. Tato možnost je ve výchozím nastavení zakázána jako přidaná vrstva ochrany pro váš počítač, ale v případě, že se jedná o osvědčené postupy zabezpečení, nebude mít počítač k dispozici žádný náchylný ke virům.

 Nejlepší ochranou před viry v makrech Office je spouštění Office na vysoké nebo velmi vysoké úrovni zabezpečení, k důvěřování pouze makrům z ověřených, známých zdrojů a k udržení aktuálnosti aktualizací zabezpečení a skenerů virů.

 Můžete povolit nebo zakázat možnost **důvěřovat přístup k Visual Basic projektu** ručně.

 Pokud se zobrazí chyby VBA nebo COM, můžete opravit instalaci Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Povolení nebo zakázání přístupu k projektům Visual Basic

1. Klikněte na kartu **soubor** .

2. Klikněte na tlačítko **Možnosti**.

3. Klikněte na **Centrum zabezpečení**a pak klikněte na **Nastavení centra zabezpečení**.

4. V **Centru zabezpečení**klikněte na **Nastavení maker**.

5. Zaškrtněte nebo zrušte kontrolu **přístupu důvěryhodnosti k objektovému modelu projektu VBA** , abyste povolili nebo zakázali přístup k Visual Basic projektům.

6. Klikněte na **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Povolení nebo zakázání přístupu k Visual Basic projektům pomocí systém Microsoft Office systému 2007

1. V nabídce **nástroje** ve Wordu nebo Excelu přejděte na **makro**a pak klikněte na **zabezpečení**.

2. V dialogovém okně **zabezpečení** klikněte na kartu **Důvěryhodní vydavatelé** .

3. Vyberte, chcete-li zakázat, nebo zrušte zaškrtnutí, pokud chcete povolit **přístup k Visual Basic projektu**.

4. Klikněte na **OK**.

## <a name="to-set-your-office-macro-security-level"></a>Nastavení úrovně zabezpečení maker Office

1. Klikněte na kartu **soubor** .

2. Klikněte na tlačítko **Možnosti**.

3. Klikněte na **Centrum zabezpečení**a pak klikněte na **Nastavení centra zabezpečení**.

4. V **Centru zabezpečení**klikněte na **Nastavení maker**.

5. V části **Nastavení makra** vyberte požadované nastavení.

6. Klikněte na **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Nastavení úrovně zabezpečení maker Office pomocí 2007 systém Microsoft Office systému

1. V nabídce **nástroje** ve Wordu nebo Excelu přejděte na **makro**a pak klikněte na **zabezpečení**.

2. Na kartě **úroveň zabezpečení** vyberte požadované nastavení.

    Karta **úroveň zabezpečení** obsahuje podrobnosti o každé úrovni. Další informace najdete v tématu "úrovně zabezpečení maker" v nápovědě pro Office.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Instalace jazyka VBA se systémem 2007 systém Microsoft Office

1. V Ovládacích panelech spusťte ovládací panel **Přidat nebo odebrat programy** nebo **programy a funkce**.

2. V seznamu **aktuálně nainstalovaných programů** vyberte Office.

3. Klikněte na **Změnit**.

4. Vyberte **Přidat nebo odebrat funkce**a potom klikněte na **pokračovat**.

5. Vyberte možnost **zvolit pokročilé přizpůsobení aplikací**a potom klikněte na tlačítko **Další**.

6. V seznamu **zvolit možnosti aktualizace pro aplikace a nástroje** rozbalte položku **sdílené funkce sady Office** .

7. Otevřete rozevírací nabídku vedle **jazyk Visual Basic for Application**a pak klikněte na **Spustit z tohoto počítače**.

8. Klikněte na **Pokračovat**.

9. Klikněte na **Zavřít**.

## <a name="to-repair-your-installation-of-office"></a>Oprava instalace Office

1. V Ovládacích panelech spusťte ovládací panel **Přidat nebo odebrat programy** nebo **programy a funkce**.

2. V seznamu **aktuálně nainstalovaných programů** vyberte svou verzi Office.

3. Klikněte na **Změnit**.

4. Vyberte **přeinstalovat nebo opravit**a pak klikněte na **Další**.

5. **V instalaci Office vyberte rozpoznat a opravit chyby**a pak klikněte na **nainstalovat**.

## <a name="see-also"></a>Viz také
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
