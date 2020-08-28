---
title: 'Kurz Docker – část 9: nasazení do cloudu'
description: Nasaďte aplikaci Docker do cloudové služby pro hostování.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 661f9f6833b5ac5d42aacde7f228b042bef00bb0
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2020
ms.locfileid: "89039037"
---
# <a name="deploy-to-the-cloud"></a>Nasazení do cloudu

Teď, když máte aplikaci spuštěnou místně, si můžete začít představit, že ji budete spouštět v cloudu, aby k ní měli přístup další lidé a mohli k nim využít. K tomu budete používat kontexty Docker. Kontext je místo, kde aktuálně pracujete s kontejnery. V současné době máte jenom svůj "výchozí" kontext, takže budete muset přidat Cloud a nasadit do něj svoji aplikaci.

## <a name="create-your-cloud-context"></a>Vytvoření kontextu cloudu

1. Chcete-li začít, můžete zjistit, jaké kontexty máte, v části kontexty na panelu Docker:

   ![Zobrazuje pouze výchozí kontext.](media/defaultcontext.png)

Měli byste se podívat jenom na výchozí kontext pro místní práci.

1. Chcete-li provést nasazení do cloudu, je třeba vytvořit nový kontext ACI, ale k tomu, abyste mohli ověřit pomocí Azure, musíte nejprve použít rozšíření účtu Azure.

   ![Přidává se rozšíření Azure](media/addazureextension.png)

Pokud ještě nemáte účet Azure, budete ho muset nastavit.

1. Nyní můžete vytvořit nový ACI kontext. To můžete provést kliknutím na tlačítko plus v části **kontexty** zobrazení Docker.

   ![Vytváření kontextu ACI](media/createnewcontext.png)

Zobrazí se vám dotaz na skupinu prostředků, ve které chcete tyto kontejnery spustit. Buď vyberte existující skupinu pomocí kláves se šipkami, nebo použijte výchozí možnost pro použití nové skupiny.

![Výběr skupiny prostředků](media/selectresourcegroup.png)

Teď můžete vidět svůj kontext ACI a kliknout na něj pravým tlačítkem, aby byl aktuální fokus/kontext použití:

![Je možné vybrat nový kontext ACI.](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Spouštění kontejnerů v cloudu

1. Nyní použijte svůj kontext ACI a spusťte kontejner.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Pokud to chcete provést, podívejte se nyní na kontejner v kontextu.

   ![Kontejner spuštěný ve vašem ACI kontextu](media/contextcontainer.png)

1. Chcete-li tuto kontrolu ověřit správně, můžete kliknout pravým tlačítkem na běžící kontejner a zvolit **Zobrazit v prohlížeči**.

   ![Kontejner v ACI s veřejnou IP adresou](media/containerinaci.png)

A vidíte, že kontejner je spuštěný ve veřejné IP adrese a funguje správně.

1. Nyní se můžete podívat na náš běžící kontejner, abyste viděli, jak funguje. Můžete začít tím, že se podíváte na protokoly kontejnerů:
 
 ```bash
   docker logs distracted-jackson
   ```

1. Do svého kontejneru můžete také pomocí místního kontejneru Exec.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Nakonec můžete jednoduše vyčistit pracovní prostor a ověřit, že se vám neúčtují průběžné spouštění kontejneru testů, stačí kliknout pravým tlačítkem na běžící kontejner a vybrat **Odebrat**.

## <a name="recap"></a>Rekapitulace

Fantastická jste nyní nastavili úlohu a nasadili ji do cloudu poprvé. To všechno můžete provést z příkazového řádku i v rámci kontextu ACI pomocí `docker run` a také pomocí `docker compose up` ke spouštění aplikací s více kontejnery. Pokud chcete získat další informace o spuštění kontejnerů v cloudu, přečtěte si rozšířenou [dokumentaci k používání ACI](https://docs.docker.com/engine/context/aci-integration/).

## <a name="next-steps"></a>Další kroky

Pokračujte v tomto kurzu.

> [!div class="nextstepaction"]
> [Co dál](whats-next.md)
