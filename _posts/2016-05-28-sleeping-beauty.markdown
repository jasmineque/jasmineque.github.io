---
layout: post
title: Java Calendar Data
date: 2018-07-05 17:15
comments: true
external-url:
categories: Java Programming
---

{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Five calendar-related classes\n",
    "\n",
    "* **`java.time.LocalDateTime`**\n",
    "* **`java.time.LocalDate`**\n",
    "* **`java.time.LocalTime`**\n",
    "* **`java.time.format.DateTimeFormatter`**\n",
    "* **`java.time.Period`**\n",
    "* **`java.time.temporal.TemporalAmount`**\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "LocalDate date1 = LocalDate.of(2017, 1, 31);\n",
    "\tPeriod period1 = Period.ofMonths(1);\n",
    "\tSystem.out.println(date1);\n",
    "    // 2017-01-31\n",
    "\tdate1.plus(period1);            // new value is lost: calendar-related objects are immutable\n",
    "\tSystem.out.println(date1);\n",
    "    // 2017-01-31\n",
    "\tLocalDate date2 = date1.plus(period1);\n",
    "\tSystem.out.println(date2);\n",
    "    // 2017-02-28"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Factory Classes\n",
    "\n",
    "Is the class that has no public constructors and provides at least one `public static` method that can create new instances of the class.\n",
    "\n",
    "Any method that is invoked to get a new instance of the class is called a __factory method__.\n",
    "\n",
    "Some `static` methods that create and return a new instance in the `LocalDate` class:\n",
    "\n",
    "    from()\n",
    "    now()\n",
    "    of()\n",
    "    ofEpochDay()\n",
    "    ofYearDay()\n",
    "    parse()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "LocalDateTime d1 = new LocalDateTime();   // won't compile"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Your birthday is: 1934-01-20\n",
      "a SATURDAY\n"
     ]
    }
   ],
   "source": [
    "import java.time.*;\n",
    "LocalDate bday = LocalDate.of(1934, 01, 20);\n",
    "\t\t\n",
    "\t\tSystem.out.println(\"Your birthday is: \" + bday);\n",
    "\t\tSystem.out.println(\"a \" + bday.getDayOfWeek());"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {},
   "outputs": [],
   "source": [
    "import java.time.temporal.ChronoUnit;\n",
    "Period p1 = Period.between(bday, LocalDate.now());\n",
    "\t\t\n",
    "\t\tSystem.out.println(\"You've lived for: \");\n",
    "\t\tSystem.out.print(p1.getDays() + \" days, \");\n",
    "\t\tSystem.out.print(p1.getMonths() + \" months, \");\n",
    "\t\tSystem.out.print(p1.getYears() + \" years\");"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Jun 15, 2018\n",
      "Fr Jun 15, 2018 n. Chr.\n",
      "11:54:19 42859365 AM\n"
     ]
    }
   ],
   "source": [
    "import java.time.*;\n",
    "import java.time.format.*;\n",
    "\n",
    "DateTimeFormatter f1 = DateTimeFormatter.ofPattern(\"MMM dd, yyyy\");\n",
    "DateTimeFormatter f2 = DateTimeFormatter.ofPattern(\"E MMM dd, yyyy G\");\n",
    "DateTimeFormatter tf1 = DateTimeFormatter.ofPattern(\"k:m:s A a\");\n",
    "\n",
    "LocalDate d = LocalDate.now();\n",
    "String s = d.format(f1);\n",
    "\n",
    "System.out.println(s);\n",
    "System.out.println(d.format(f2));\n",
    "\n",
    "LocalTime t = LocalTime.now();\n",
    "System.out.println(t.format(tf1));"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "SciJava",
   "language": "groovy",
   "name": "scijava"
  },
  "language_info": {
   "codemirror_mode": "groovy",
   "file_extension": "",
   "mimetype": "",
   "name": "scijava",
   "nbconverter_exporter": "",
   "pygments_lexer": "groovy",
   "version": "1.0"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
