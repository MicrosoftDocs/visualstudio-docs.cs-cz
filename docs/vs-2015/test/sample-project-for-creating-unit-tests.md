---
title: Ukázkový projekt pro vytváření testů jednotek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d495d0bf12c900d34a04a84e950b002494b7b5c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660400"
---
# <a name="sample-project-for-creating-unit-tests"></a>Ukázkový projekt testů jednotek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento vzorový kód je k dispozici pro použití v následujících návodech:

- [Návod: vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Tento návod vás provede kroky k vytvoření a přizpůsobení testů jednotek, jejich spuštění a prohlédnutí výsledků testu.

- [Návod: spuštění testů a zobrazení pokrytí kódu](https://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8). Tento návod ukazuje, jak zobrazit data o pokrytí kódu, která zobrazují podíl testovaného kódu projektu.

- [Návod: použití nástroje pro testování z příkazového řádku](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867). V tomto návodu použijete nástroj MSTest.exe příkazového řádku pro spuštění testů a zobrazení výsledků.

## <a name="sample-code"></a>Příklad kódu
 Jedinou záměrné chybou v této ukázce je, že v metodě debet "m_balance + = částka" by měl být znaménko minus a znaménko plus před znaménkem rovná se.

```
using System;

namespace BankAccountNS
{
    /// <summary>
    /// Bank Account demo class.
    /// </summary>
    public class BankAccount
    {
        private string m_customerName;

        private double m_balance;

        private bool m_frozen = false;

        private BankAccount()
        {
        }

        public BankAccount(string customerName, double balance)
        {
            m_customerName = customerName;
            m_balance = balance;
        }

        public string CustomerName
        {
            get { return m_customerName; }
        }

        public double Balance
        {
            get { return m_balance; }
        }

        public void Debit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount > m_balance)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount; // intentionally incorrect code
        }

        public void Credit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount;
        }

        private void FreezeAccount()
        {
            m_frozen = true;
        }

        private void UnfreezeAccount()
        {
            m_frozen = false;
        }

        public static void Main()
        {
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

            ba.Credit(5.77);
            ba.Debit(11.22);
            Console.WriteLine("Current balance is ${0}", ba.Balance);
        }

    }
}
```

 /* Ukázkové společnosti, organizace, produkty, názvy domén, e-mailové adresy, loga, osoby, místa a události použité v ukázkách jsou smyšlené.  Žádná spojitost se skutečnou společností, organizací, produktem, názvem domény, e-mailovou adresou, logem, osobou, místem a událostmi není zamýšlená nebo by se měla odvodit. \*/

## <a name="working-with-the-code"></a>Práce s kódem
 Pro práci s tímto kódem je nejprve nutné pro něj vytvořit projekt v sadě [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Postupujte podle kroků v části "Příprava návodu" v [návodu: vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="see-also"></a>Viz také
 [Návod: vytvoření a spuštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) [: spustit testy a zobrazit návod k pokrytí kódu](https://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8) [: použití nástroje pro testování z příkazového řádku](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)
