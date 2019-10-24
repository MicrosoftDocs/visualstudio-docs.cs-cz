---
title: Omezení ladění WCF | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c70195cdc0a6a03395744c63f556ce8c2970aa30
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731509"
---
# <a name="limitations-on-wcf-debugging"></a>Omezení ladění WCF
Existují tři způsoby, jak můžete začít s laděním služby WCF:

- Ladíte klientský proces, který volá službu. Ladicí program kroky do služby. Služba nemusí být ve stejném řešení jako vaše klientská aplikace.

- Ladíte klientský proces, který vytváří požadavek na službu. Služba musí být součástí vašeho řešení.

- Pomocí **připojit k procesu** se připojíte ke službě, která je aktuálně spuštěná. Ladění začíná v rámci služby.

  V tomto tématu jsou popsána omezení těchto scénářů.

## <a name="limitations-on-stepping-into-a-service"></a>Omezení krokování na službu
 Pro krokování služby z klientských aplikací, které ladíte, musí být splněny následující podmínky:

- Klient musí volat službu pomocí synchronního objektu klienta.

- Operace kontraktu nemůže být jednosměrná.

- Pokud je server asynchronní, nemůžete zobrazit plný zásobník volání při provádění kódu uvnitř služby.

- Ladění musí být povoleno s následujícím kódem v souboru App. config nebo Web. config:

    ```xml
    <system.web>
      <compilation debug="true" />
    </system.web>
    ```

     Tento kód se musí přidat jenom jednou. Tento kód můžete přidat úpravou souboru. config nebo připojením ke službě pomocí **připojit k procesu**. Použijete **-li ke zpracování ve službě připojit k procesu** , kód ladění je automaticky přidán do souboru. config. Potom můžete do služby ladit a krokovat bez nutnosti upravovat soubor. config.

## <a name="limitations-on-stepping-out-of-a-service"></a>Omezení krokování ze služby
 Krokování ze služby a zpátky na klienta má stejná omezení, která jsou popsaná pro krokování do služby. Kromě toho musí být ladicí program připojen ke klientovi. Při ladění klienta a krokování do služby zůstane ladicí program připojen ke službě. To platí bez ohledu na to, jestli jste klienta spustili pomocí možnosti **Spustit ladění** nebo připojit k klientovi pomocí možnosti **připojit k procesu**. Pokud jste zahájili ladění připojením ke službě, ladicí program ještě není připojen ke klientovi. V takovém případě, pokud musíte krok ze služby a zpátky na klienta, musíte nejprve použít **připojit k procesu** a připojit se k klientovi ručně.

## <a name="limitations-on-automatic-attach-to-a-service"></a>Omezení automatického připojení ke službě
 Automatické připojení ke službě má následující omezení:

- Služba musí být součástí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] řešení, které ladíte.

- Služba musí být hostovaná. Může být součástí projektu webu (systém souborů a HTTP), projektu webové aplikace (systému souborů a protokolu HTTP) nebo projektu knihovny služby WCF. Projekty knihovny služby WCF můžou být buď knihovny služeb nebo knihovny služby pracovního postupu.

- Služba musí být vyvolána z klienta WCF.

- Ladění musí být povoleno s následujícím kódem v souboru App. config nebo Web. config:

  ```xml
  <system.web>
    <compilation debug="true" />
  <system.web>
  ```

## <a name="self-hosting"></a>Samoobslužné hostování
 *Samoobslužná služba* je služba WCF, která neběží ve službě IIS, hostiteli služby WCF nebo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] vývojový server. Informace o tom, jak ladit samoobslužné služby, naleznete v tématu [How to: Debug a on-Hosted Service WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md).

## <a name="self-hosting"></a>Samoobslužné hostování
 Chcete-li povolit ladění aplikací [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3,0 nebo 3,5, je nutné před instalací [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] nainstalovat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3,0 nebo 3,5. Pokud je [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] nainstalován před [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3,0 nebo 3,5, dojde k chybě při pokusu o ladění aplikace [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3,0 nebo 3,5. Chybová zpráva: "nelze automaticky krokovat se serverem." Chcete-li tento problém vyřešit, opravte instalaci [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] pomocí **ovládacího panelu** Windows  > **programy a funkce** .

## <a name="see-also"></a>Viz také:
- [Ladění služeb WCF](../debugger/debugging-wcf-services.md)
- [Postupy: Ladění služby WCF s vlastním hostováním](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
