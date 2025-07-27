// BudidayaAgribisnisApp.jsx
// Full Stack MVP (Frontend Only - React Template)

import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";
import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs";
import { BarChart, Bar, XAxis, YAxis, Tooltip, ResponsiveContainer } from "recharts";

const dummyData = [
  { name: "Jan", income: 1500000, expense: 1000000 },
  { name: "Feb", income: 1800000, expense: 1200000 },
  { name: "Mar", income: 2000000, expense: 1300000 },
];

export default function BudidayaAgribisnisApp() {
  const [usaha, setUsaha] = useState({ nama: "", jenis: "", luas: "" });

  const handleChange = (e) => {
    setUsaha({ ...usaha, [e.target.name]: e.target.value });
  };

  return (
    <div className="p-6 max-w-4xl mx-auto space-y-6">
      <h1 className="text-3xl font-bold">Sistem Informasi Budidaya Pertanian</h1>

      <Tabs defaultValue="data" className="w-full">
        <TabsList>
          <TabsTrigger value="data">Data Usaha</TabsTrigger>
          <TabsTrigger value="grafik">Grafik Keuangan</TabsTrigger>
        </TabsList>

        <TabsContent value="data">
          <Card className="mt-4">
            <CardContent className="space-y-4 p-4">
              <Input
                placeholder="Nama Usaha"
                name="nama"
                value={usaha.nama}
                onChange={handleChange}
              />
              <Input
                placeholder="Jenis Budidaya (contoh: Cabai, Padi)"
                name="jenis"
                value={usaha.jenis}
                onChange={handleChange}
              />
              <Input
                placeholder="Luas Lahan (Ha)"
                name="luas"
                value={usaha.luas}
                onChange={handleChange}
              />
              <Button>Simpan Data</Button>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="grafik">
          <Card className="mt-4">
            <CardContent className="p-4">
              <h2 className="text-xl font-semibold mb-4">Laporan Bulanan</h2>
              <ResponsiveContainer width="100%" height={300}>
                <BarChart data={dummyData}>
                  <XAxis dataKey="name" />
                  <YAxis />
                  <Tooltip />
                  <Bar dataKey="income" fill="#16a34a" name="Pendapatan" />
                  <Bar dataKey="expense" fill="#dc2626" name="Pengeluaran" />
                </BarChart>
              </ResponsiveContainer>
            </CardContent>
          </Card>
        </TabsContent>
      </Tabs>
    </div>
  );
}
