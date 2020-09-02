---
title: 'Postupy: ověření nastavení vlastnosti služby IIS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ac2ce4f823d82d8a0d8569e15c4ba8920d91d36c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686836"
---
# <a name="how-to-verify-iis-property-settings"></a>Postupy: Ověření nastavení vlastnosti služby IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nastavit vlastnosti webové aplikace pomocí nástroje pro správu služby IIS. Tyto vlastnosti musí být správně nastaveny, aby bylo možné aplikaci spustit, takže ověřování těchto nastavení je často nezbytným krokem při řešení potíží.  
  
> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Postup kontroly nastavení služby IIS pro webovou aplikaci  
  
1. Otevřete okno **Nástroje pro správu** : v nabídce **Start** přejděte na **programy**a potom klikněte na **Nástroje pro správu**. Pokud se **Nástroje pro správu** nezobrazí v nabídce **programy** , pak je vyhledejte v **Ovládacích panelech**.  
  
    - V systému Windows 2000 vyberte možnost **Správce služeb Internetu**.  
  
    - V systému Windows XP vyberte možnost **Internetová informační služba**.  
  
    - V systému Windows Server 2003 poklikejte na **Správa serveru**.  
  
         Otevře se okno **Správa serveru** . V části **aplikační server**klikněte na **Spravovat tento aplikační server**.  
  
         Otevře se okno **aplikační server** . V levém podokně otevřete uzel **správce Internetová informační služba (IIS)** .  
  
2. V dialogovém okně klikněte na uzel ovládacího prvku strom pro váš počítač. Klikněte na uzel **webové servery** a vyberte uzel webové aplikace. Bude se jednat buď o uzel webu, a tedy na stejné úrovni **jako výchozí** uzel webu nebo na uzlu virtuálního adresáře pod existujícím uzlem webu.  
  
3. Klikněte pravým tlačítkem myši na webovou aplikaci a v místní nabídce klikněte na **vlastnosti**.  
  
4. Ověřte nastavení zabezpečení webové aplikace:  
  
    1. V okně **vlastnosti** webové aplikace klikněte na kartu **zabezpečení adresáře** a pak klikněte na **Upravit**.  
  
    2. V dialogovém okně **metody ověřování** vyberte možnost **Povolit anonymní přístup** a **integrované ověřování systému Windows** , pokud již nejsou vybrány.  
  
    3. Kliknutím na tlačítko **OK** zavřete dialogové okno **metody ověřování** .  
  
5. V případě serverové aplikace ATL ověřte, zda je příkaz LADIT přidružen k vašemu rozšíření ISAPI. Další informace naleznete v tématu [How to: přidružte příkaz ladění s příponou](https://msdn.microsoft.com/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6. V případě [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace se ujistěte, že virtuální složka aplikace má název aplikace nastavený ve **Správci Internetová informační služba (IIS)** **Správce služeb Internetu** nebo **Internetová informační služba**.  
  
    1. V okně **vlastnosti** webové aplikace vyberte kartu **adresář** , pokud je aplikace ve virtuálním adresáři nebo na kartě **domovského adresáře** , pokud je aplikace na webu.  
  
    2. Ověřte, že název v **místní cestě** odpovídá názvu adresáře, ve kterém byla aplikace skutečně nasazena.  
  
    3. V části **nastavení aplikace**zadejte název kořenového adresáře, který obsahuje aplikaci.  
  
    4. Kliknutím na tlačítko **OK** zavřete dialogové okno **vlastnosti** .  
  
7. V případě [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace klikněte na kartu **ASP.NET** a ověřte, zda je zadána správná verze systému [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
8. Kliknutím na tlačítko **OK** zavřete dialogové okno **vlastnosti** .  
  
9. Kliknutím na tlačítko **OK** zavřete dialogové okno **Internetová informační služba (Správce služby IIS)**, **Správce služeb Internetu**nebo **Internetová informační služba** .  
  
## <a name="see-also"></a>Viz také  
 [Řešení potíží](../debugger/debugging-web-applications-troubleshooting.md)
