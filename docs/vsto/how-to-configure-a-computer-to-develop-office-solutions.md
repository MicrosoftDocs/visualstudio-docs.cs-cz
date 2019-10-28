---
title: 'Postupy: Konfigurace počítače pro vývoj řešení pro systém Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb29dc4151bc457eb60ce836986817bc1b0137c9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985965"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Postupy: Konfigurace počítače pro vývoj řešení pro systém Office
  Pro konfiguraci vývojového počítače, abyste mohli používat nástroje systém Microsoft Office Developer Tools v aplikaci Visual Studio, postupujte podle pokynů v tomto tématu. K provedení těchto kroků musíte mít ve vývojovém počítači oprávnění správce.

### <a name="to-configure-the-development-computer"></a>Konfigurace vývojového počítače

1. Nainstalujte verzi sady Visual Studio, která obsahuje nástroje Office Developer Tools. Nástroje Office Developer Tools jsou nainstalovány ve výchozím nastavení. Pokud přizpůsobíte instalaci sady Visual Studio výběrem funkcí, které chcete nainstalovat, ujistěte se, že je při instalaci vybrána možnost **systém Microsoft Office vývojářské nástroje** . Další informace o verzích sady Visual Studio, které obsahují nástroje Office Developer Tools, najdete v tématu [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

2. Nainstalujte verzi Office, která je podporovaná vývojářskými nástroji Office v sadě Visual Studio. Další informace najdete v tématu [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

     Ujistěte se, že instalujete také PIA pro verzi systému Office, kterou nainstalujete. PIA se ve výchozím nastavení instalují s Office. Pokud upravíte instalační program sady Office, ujistěte se, že je pro aplikace, na kterou chcete cílit, vybraná funkce **Podpora programovatelnosti rozhraní .NET** .

3. Máte-li anglickou verzi sady Visual Studio, ale používáte jiné než anglické nastavení systému Windows, můžete nainstalovat [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jazykové sady a zobrazit [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zprávy ve stejném jazyce jako Windows. Jazykové sady v jiné než anglické verzi sady Visual Studio automaticky instalují. Jazyková sada je k dispozici na [webu Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Viz také:

- [Začínáme &#40;s vývojem pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Postupy: instalace redistribuovatelného prostředí Visual Studio Tools for Office runtime](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Postupy: instalace primárních sestavení vzájemné spolupráce pro systém Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
