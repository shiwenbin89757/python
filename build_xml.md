<?xml version="1.0"  encoding="UTF-8"?>

<project name="Service_360" basedir="." default="war">
    <property environment="env" />
    <property name="project.root" value="${basedir}"/>
    <property name="project.name" value="Service_360"/>
    <property file="build.properties"/>
	
    <!-- 代码目录 -->
    <property name="src.dir" value="${project.root}"/>
    <property name="src.jsp.dir" value="${src.dir}/WebContent"/>
	<property name="src.lib.dir" value="${src.dir}/WebContent/WEB-INF/lib"/>

    <!-- 临时编译目录 -->
    <property name="build.dir" value="${src.dir}/WebContent/WEB-INF"/>
	<!--根据本地实际情况自行修改路径-->
    <property name="build.lib.dir" value="F:\tomcat\apache-tomcat-8.5.29\lib"/>
    <property name="build.classes.dir" value="${build.dir}/classes" />

		
    <!-- Java编译CLASSPATH -->
    <path id="master-classpath">
    	<fileset dir="${src.lib.dir}" />
    	<fileset dir="${build.lib.dir}" />
    </path>

    <target name="clean" description="清空所有输出文件包括build和部署目录">
        <delete dir="${build.classes.dir}"/>
    </target>
    
	<target name="init" depends="clean" description="创建目录" >
		<mkdir dir="${build.classes.dir}" />
	</target>    

    <target name="compile" depends="init" description="编译Java文件">
    	<javac destdir="${build.classes.dir}"  target="1.7" debug="true" deprecation="false" optimize="false"  encoding="UTF-8"  includeAntRuntime="false" failonerror="true">
		<src path="${src.dir}/src"/>
    	<classpath refid="master-classpath"/>
      </javac>
    </target>

    <!-- =================================================================== -->
    <!-- 创建WAR应用-->
    <!-- =================================================================== -->
    <target name="war" depends="compile" description="创建WAR应用">
    	<copy todir="${build.classes.dir}">
    		<fileset dir="${src.dir}/src">
    			<include name="*.properties"/>
    		 </fileset>
    	</copy>
    	<war destfile="${project.root}/${project.name}.war" webxml="${build.dir}/web.xml" >
        	<fileset dir="${src.jsp.dir}"></fileset>
    	</war>
    	
    </target>

    <!-- =================================================================== -->
    <!-- 帮助信息 -->
    <!-- =================================================================== -->
    <target name="usage">
        <echo message="Pafa Application Build File"/>
        <echo message="用法：ant -[target]"/>
        <echo message="------------------------------------------------------"/>
        <echo message="[target]"/>
        <echo message="clean        --> 清空所有输出文件包括build和部署目录"/>
        <echo message="compile      --> 编译Java文件"/>
        <echo message="war          --> 创建用于发布的WAR包文件（配置文件已提出）"/>
        <echo message="exploded-ear --> 创建展开目录形式的EAR应用(开发模式)"/>
        <echo message="------------------------------------------------------"/>
    </target>
</project>