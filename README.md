import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs"; import { LineChart, Line, XAxis, YAxis, Tooltip, ResponsiveContainer } from "recharts"; import { useEffect, useState } from "react";

export default function TheWhimsHub() { const [stockData, setStockData] = useState([]);

useEffect(() => { // Simulated fetch of real-time data (replace with real API call) const fetchData = async () => { const todayData = [ { name: "EABL", value: 188 }, { name: "BAT", value: 518 }, { name: "KCB", value: 129 }, { name: "Equity", value: 144 }, { name: "Jubilee", value: 241 }, ]; setStockData(todayData); };

fetchData();

}, []);

return ( <div className="p-6 bg-gradient-to-br from-green-200 via-white to-purple-100 min-h-screen text-gray-800"> <header className="text-center mb-6"> <h1 className="text-4xl font-bold text-green-800">THE WHIMS HUB</h1> <p className="text-sm italic text-blue-700">Where Youth Meets Strategy — Insight by Design</p> </header>

<Tabs defaultValue="insights" className="w-full max-w-5xl mx-auto">
    <TabsList className="grid grid-cols-4 bg-white shadow rounded-xl mb-4">
      <TabsTrigger value="insights">Insights</TabsTrigger>
      <TabsTrigger value="watchlist">Watchlist</TabsTrigger>
      <TabsTrigger value="tools">Smart Tools</TabsTrigger>
      <TabsTrigger value="startups">Startups & ESG</TabsTrigger>
    </TabsList>

    <TabsContent value="insights">
      <Card>
        <CardContent className="p-4">
          <h2 className="text-xl font-semibold text-purple-700 mb-2">📊 Today's Strategy Snapshot</h2>
          <p>Market dip in telecoms. Financials and consumer staples show strength. Watch EABL, BAT, NCBA.</p>
        </CardContent>
      </Card>
    </TabsContent>

    <TabsContent value="watchlist">
      <Card>
        <CardContent className="p-4">
          <h2 className="text-xl font-semibold text-green-700 mb-2">📈 Stock Watchlist</h2>
          <ResponsiveContainer width="100%" height={300}>
            <LineChart data={stockData}>
              <XAxis dataKey="name" />
              <YAxis />
              <Tooltip />
              <Line type="monotone" dataKey="value" stroke="#4C1D95" strokeWidth={2} />
            </LineChart>
          </ResponsiveContainer>
        </CardContent>
      </Card>
    </TabsContent>

    <TabsContent value="tools">
      <Card>
        <CardContent className="p-4 space-y-2">
          <h2 className="text-xl font-semibold text-blue-700">🧠 Smart Tools</h2>
          <Button variant="outline">📅 Economic Calendar</Button>
          <Button variant="outline">📊 ROI Calculator</Button>
          <Button variant="outline">🔔 Set Stock Alerts</Button>
        </CardContent>
      </Card>
    </TabsContent>

    <TabsContent value="startups">
      <Card>
        <CardContent className="p-4">
          <h2 className="text-xl font-semibold text-purple-700">🌱 Green Startups & Konza</h2>
          <ul className="list-disc list-inside text-sm">
            <li>Track M-KOPA, Upepo Energy, PowerHive</li>
            <li>Follow Konza Technopolis ESG projects</li>
            <li>Subscribe to green grant alerts</li>
          </ul>
        </CardContent>
      </Card>
    </TabsContent>
  </Tabs>

  <footer className="text-center text-xs text-gray-500 mt-8">
    Logo: Silhouette Inspired by Light Yagami • Powered by AI Supervision
  </footer>
</div>

); }

