---
title: 'Postupy: ověření nastavení vlastnosti služby IIS | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f98796a7fd9546c8377eefcc4ad25fb90e549544
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389484"
---
# <a name="how-to-verify-iis-property-settings"></a>Postupy: Ověření nastavení vlastnosti služby IIS

Můžete nastavit vlastnosti pro webovou aplikaci pomocí nástroje pro správu služby IIS. Tyto vlastnosti musí být správně nastavena pro spuštění, aplikace tak, že ověřování těchto nastavení je často nezbytným krokem při řešení potíží.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [Resetovat nastavení](../ide/environment-settings.md#reset-settings).

## <a name="to-check-iis-settings-for-the-web-application"></a>Zkontrolujte nastavení služby IIS pro webovou aplikaci

1. Otevřít **nástroje pro správu** okna: na **Start** nabídky, přejděte na **programy**a potom klikněte na tlačítko **nástroje pro správu**. Pokud **nástroje pro správu** se nezobrazují v **programy** nabídky a pak vyhledejte ho **ovládací panely**.

   -   Ve Windows 2000, vyberte **Správce služeb Internetu**.

   -   Na Windows XP, vyberte **Internetová informační služba**.

   -   V systému Windows Server 2003, dvakrát klikněte na panel **Správa serveru**.

        **Správa serveru** otevře se okno. V části **aplikační Server**, klikněte na tlačítko **spravovat tento aplikační server**.

        **Aplikační Server** otevře se okno. Otevřít **Správce Internetové informační služby (IIS)** uzlu v levém podokně.

2. V dialogovém okně klikněte na uzel stromu ovládacích prvků pro váš počítač. Klikněte na tlačítko **weby** uzel a vyberte uzel webové aplikace. Buď bude uzel webu a proto na stejné úrovni **výchozí webový server** uzlu nebo virtuální adresář uzel pod existující uzel webu.

3. Klikněte pravým tlačítkem na webovou aplikaci a v místní nabídce klikněte na tlačítko **vlastnosti**.

4. Ověřte nastavení zabezpečení pro webové aplikace:

   1.  Ve webové aplikaci **vlastnosti** okna, klikněte na tlačítko **zabezpečení adresáře** kartu a klikněte na tlačítko **upravit**.

   2.  V **metody ověřování** dialogu **povolit anonymní přístup** a **ověření integrované Windows** Pokud ještě nejsou vybraná.

   3.  Klikněte na tlačítko **OK** zavřete **metody ověřování** dialogové okno.

5. Pro aplikaci knihovny ATL Server ověřte, zda je příkaz DEBUG. přidružený rozšíření ISAPI. Další informace najdete v tématu [postupy: přidružení ladění operaci s rozšířením](https://msdn.microsoft.com/library/50d261d3-4bd4-41c0-b44e-3591086f121e).

6. Pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace, ujistěte se, že virtuální složka pro aplikace má název aplikace v **Správce Internetové informační služby (IIS)**, **Správce služeb Internetu** nebo  **Internetová informační služba**.

   1.  Ve webové aplikaci **vlastnosti** okna, vyberte **Directory** kartu, pokud je aplikace ve virtuálním adresáři, nebo **domovský adresář** kartu, pokud je aplikace Adresa webové stránky.

   2.  Ověřte, že název v **místní cesta** odpovídá názvu adresáře, ve skutečnosti nasazená aplikace.

   3.  V části **nastavení aplikace**, zadejte název kořenového adresáře, který obsahuje aplikace.

   4.  Klikněte na tlačítko **OK** zavřete **vlastnosti** dialogové okno.

7. Pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace, klikněte na tlačítko **ASP.NET** kartě a ověřte, že správnou verzi [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] je zadán.

8. Klikněte na tlačítko **OK** zavřete **vlastnosti** dialogové okno.

9. Klikněte na tlačítko **OK** zavřete **Správce Internetové informační služby (IIS)**, **Správce služeb Internetu**, nebo **Internetová informační služba**dialogové okno.

## <a name="see-also"></a>Viz také:

- [Odstraňování potíží](../debugger/debugging-web-applications-troubleshooting.md)